# GameBanana API - Best Practices

> Guidelines for reliable and efficient API usage

---

## Rate Limiting

### Recommended Limits

| Request Type | Max Requests | Wait Time |
|--------------|--------------|-----------|
| Search | 10/second | 100ms |
| Detail fetch | 20/second | 50ms |
| Bulk downloads | 5/second | 200ms |

### Implementation

```python
import time
import requests
from threading import Lock

class RateLimiter:
    def __init__(self, max_per_second):
        self.max_per_second = max_per_second
        self.min_interval = 1.0 / max_per_second
        self.last_request = 0
        self.lock = Lock()
    
    def wait(self):
        with self.lock:
            now = time.time()
            elapsed = now - self.last_request
            if elapsed < self.min_interval:
                time.sleep(self.min_interval - elapsed)
            self.last_request = time.time()

limiter = RateLimiter(max_per_second=10)

# Usage
def api_get(url, *args, **kwargs):
    limiter.wait()
    return requests.get(url, *args, **kwargs)
```

---

## Caching

### What to Cache

| Data Type | Cache Duration |
|-----------|---------------|
| Game info | 1 hour |
| Category list | 1 hour |
| Search results | 5 minutes |
| Mod details | 15 minutes |
| User profile | 30 minutes |

### Implementation

```python
from functools import lru_cache
import time

cache = {}

def cached_request(url, ttl=300):
    """Simple cache with TTL"""
    now = time.time()
    
    if url in cache:
        cached_time, cached_data = cache[url]
        if now - cached_time < ttl:
            return cached_data
    
    response = requests.get(url)
    cache[url] = (now, response.json())
    return response.json()
```

---

## Error Handling

### Basic Pattern

```python
def safe_get(url, params=None):
    try:
        r = requests.get(url, params=params, timeout=10)
        r.raise_for_status()
        return r.json()
    except requests.exceptions.HTTPError as e:
        if e.response.status_code == 404:
            return None  # Not found
        elif e.response.status_code == 429:
            print("Rate limited!")
            time.sleep(60)
            return safe_get(url, params)  # Retry
        else:
            raise
    except requests.exceptions.RequestException as e:
        print(f"Request failed: {e}")
        return None
```

### Graceful Degradation

```python
def get_mod_safe(mod_id):
    """Try Web API first, fall back to Official"""
    
    # Try Web API
    try:
        r = requests.get(
            f"https://gamebanana.com/apiv11/Mod/{mod_id}/ProfilePage",
            timeout=5
        )
        if r.status_code == 200:
            return {"source": "web", "data": r.json()}
    except:
        pass
    
    # Fall back to Official
    try:
        r = requests.get(
            "https://api.gamebanana.com/Core/Item/Data",
            params={"itemtype": "Mod", "itemid": mod_id},
            timeout=5
        )
        if r.status_code == 200:
            return {"source": "official", "data": r.json()}
    except:
        pass
    
    return {"source": None, "data": None}
```

---

## Pagination

### Always Check Metadata

```python
def fetch_all(url_template, **params):
    """Fetch all pages"""
    results = []
    page = 1
    
    while True:
        params["_nPage"] = page
        r = requests.get(url_template, params=params).json()
        
        records = r.get("_aRecords", [])
        results.extend(records)
        
        # Check for more pages
        meta = r.get("_aMetadata", {})
        if meta.get("_bIsComplete", True):
            break
        
        page += 1
    
    return results

# Usage
all_mods = fetch_all(
    "https://gamebanana.com/apiv11/Game/4254/Subfeed",
    _nPerpage=50
)
```

---

## User Agent

### Set Proper User Agent

```python
headers = {
    "User-Agent": "MyApp/1.0 (https://myapp.com; contact@myapp.com)"
}

# Or with requests.Session
session = requests.Session()
session.headers.update(headers)
```

---

## Testing

### Mock Responses

```python
import responses

@responses.activate
def test_search():
    responses.add(
        responses.GET,
        "https://gamebanana.com/apiv11/Util/Search/Results",
        json={
            "_aMetadata": {"_nRecordCount": 1, "_bIsComplete": True},
            "_aRecords": [{"_idRow": 123, "_sName": "Test Mod"}]
        }
    )
    
    result = search_mods("test")
    assert result["_aRecords"][0]["_sName"] == "Test Mod"
```

---

## Production Checklist

- [ ] Rate limiting implemented
- [ ] Error handling for all status codes
- [ ] Request timeouts set (10s recommended)
- [ ] Appropriate caching strategy
- [ ] User-Agent header set
- [ ] Logging for debugging
- [ ] Retry logic with backoff
- [ ] Response validation

---

## Quick Reference

| Tip | Value |
|-----|-------|
| Timeout | 10 seconds |
| Max retries | 3 |
| Backoff | Exponential (2^n seconds) |
| Cache search | 5 minutes |
| Cache detail | 15 minutes |
| Rate limit | 10 req/sec |
