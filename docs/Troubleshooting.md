# Troubleshooting Guide

> Solutions for common problems

---

## Connection Issues

### "Connection timeout"

**Cause**: Server not responding or network issue

**Solution**:
```python
# Add timeout
requests.get(url, timeout=30)
```

**Still failing?** Try:
```bash
# Test manually
curl -v https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=test
```

---

### "SSL certificate error"

**Cause**: Outdated SSL/TLS

**Solution**:
```python
# Python - disable verification (not recommended for prod)
requests.get(url, verify=False)

# Or update install -- certs
pipupgrade certifi
```

---

## Response Issues

### Empty response / No data

**Cause**: Wrong parameters or API change

**Solution**:
```python
# Check response structure
print(response.json())

# Verify required params
# Most endpoints need _sModelName for search
```

### Response is HTML (not JSON)

**Cause**: Wrong URL or API changed

**Solution**:
```bash
# Wrong:
curl gamebanana.com/apiv11/...

# Correct:
curl https://gamebanana.com/apiv11/...
```

---

## Authentication Issues

### "Auth failed" / 401 errors

**Cause**: Wrong credentials or session expired

**Solution**:
```python
# For Web API - use browser session
session = requests.Session()
session.cookies.set("session_id", "your_session")

# For Official API - check API key
headers = {"ApiKey": "your_key"}
```

### "Rate limited" / 429 errors

**Cause**: Too many requests

**Solution**:
```python
import time

# Exponential backoff
for attempt in range(3):
    r = requests.get(url)
    if r.status_code == 429:
        wait = 2 ** attempt * 10
        print(f"Waiting {wait}s...")
        time.sleep(wait)
    else:
        break
```

---

## Data Issues

### Wrong game ID

**Find correct ID**:
```bash
# Search games first
curl "https://gamebanana.com/apiv11/Util/Game/NameMatch?_sName=counter-strike"
```

### Wrong mod/section type

**Valid section types**:
```
Mod, Tool, Game, Map, Texture, Sound, Script, 
Model, Skin, Concept, Wip, Tutorial, Article, 
Blog, News, Member, Studio
```

### Missing fields

**Cause**: Use ProfilePage endpoint for full data

```bash
# Basic - limited fields
curl gamebanana.com/apiv11/Mod/123

# Full - all fields  
curl gamebanana.com/apiv11/Mod/123/ProfilePage
```

---

## Pagination Issues

### Infinite loop

**Cause**: Not checking `_bIsComplete` correctly

**Fix**:
```python
# Wrong
while page < 100:  # arbitrary limit

# Correct
while not data["_aMetadata"]["_bIsComplete"]:
```

### Wrong page count

**Cause**: Not resetting params

**Fix**:
```python
params = {"_nPage": page, "_nPerpage": 50}
# Don't reuse same params object!
```

---

## File Download Issues

### Can't get file URL

**Solution**:
```bash
# Use DownloadPage endpoint
GET /Mod/123/DownloadPage

# Returns:
{
  "_aFiles": [
    {
      "_sDownloadUrl": "https://..."
    }
  ]
}
```

### ZIP tree empty

**Cause**: File ID wrong or file not archived

```bash
# Get file ID from DownloadPage first
GET /Mod/123/DownloadPage -> returns _aFiles[]._idRow

# Then use that ID
GET /File/FILE_ID
```

---

## Debug Checklist

```python
# Add this to debug
import requests

# Enable logging
import logging
logging.basicConfig()
logging.getLogger().setLevel(logging.DEBUG)
requests_log = logging.getLogger("requests.packages.urllib3")
requests_log.setLevel(logging.DEBUG)
requests_log.propagate = True

# Your request
r = requests.get(url)

# Check everything
print("URL:", r.url)
print("Status:", r.status_code)
print("Headers:", r.headers)
print("Content:", r.text[:500])
```

---

## Common Error Messages

| Error | Meaning | Fix |
|-------|---------|-----|
| `CONFLICTING_FILTERS` | Include + exclude same values | Remove one |
| `INVALID_ITEM_TYPE` | Wrong section name | Check valid types |
| `NOT_FOUND` | ID doesn't exist | Verify ID |
| `MISSING_PARAMETER` | Required param missing | Add required param |

---

## Getting Help

1. **Test with curl first** - isolate the issue
2. **Check response** - `print(r.json())`
3. **Verify URL** - no typos, correct base
4. **Check params** - required vs optional
5. **Search existing issues** - GameBanana forums

---

## Test Your Setup

```python
import requests

BASE = "https://gamebanana.com/apiv11"

def test_connection():
    # Test 1: Search
    r = requests.get(f"{BASE}/Util/Search/Results", 
                     params={"_sSearchString": "test", "_sModelName": "Mod"})
    assert r.status_code == 200, f"Search failed: {r.status_code}"
    
    # Test 2: Get game
    r = requests.get(f"{BASE}/Game/4254/ProfilePage")
    assert r.status_code == 200, f"Game failed: {r.status_code}"
    
    # Test 3: Get mod
    r = requests.get(f"{BASE}/Mod/650004/ProfilePage")
    assert r.status_code == 200, f"Mod failed: {r.status_code}"
    
    print("✓ All tests passed!")

test_connection()
```
