# Python Quick Reference

> Copy-paste code snippets for Python

---

## Setup

```python
import requests

BASE_WEB = "https://gamebanana.com/apiv11"
BASE_OFFICIAL = "https://api.gamebanana.com"

session = requests.Session()
session.headers.update({
    "User-Agent": "MyApp/1.0"
})
```

---

## Search

```python
# Search mods
def search_mods(query, game_id=None, page=1, perpage=20):
    params = {
        "_sSearchString": query,
        "_sModelName": "Mod",
        "_nPage": page,
        "_nPerpage": perpage
    }
    if game_id:
        params["_idGameRow"] = game_id
    return session.get(f"{BASE_WEB}/Util/Search/Results", params=params).json()

# Search games
def search_games(name):
    return session.get(
        f"{BASE_WEB}/Util/Game/NameMatch",
        params={"_sName": name}
    ).json()
```

---

## Get Data

```python
# Get mod details
def get_mod(mod_id):
    return session.get(f"{BASE_WEB}/Mod/{mod_id}/ProfilePage").json()

# Get game with categories
def get_game(game_id):
    return session.get(f"{BASE_WEB}/Game/{game_id}/ProfilePage").json()

# Get member
def get_member(member_id):
    return session.get(f"{BASE_WEB}/Member/{member_id}/ProfilePage").json()

# Get file (with ZIP tree!)
def get_file(file_id):
    return session.get(f"{BASE_WEB}/File/{file_id}").json()
```

---

## Lists

```python
# Latest mods
def latest_mods(page=1, perpage=20):
    return session.get(
        f"{BASE_WEB}/Mod/Index",
        params={"_nPage": page, "_nPerpage": perpage}
    ).json()

# Game submissions
def game_submissions(game_id, page=1):
    return session.get(
        f"{BASE_WEB}/Game/{game_id}/Subfeed",
        params={"_nPage": page}
    ).json()

# Featured
def featured(section="Mod"):
    return session.get(
        f"{BASE_WEB}/Util/List/Featured",
        params={"_sModelName": section}
    ).json()
```

---

## Pagination

```python
def fetch_all(url, params=None):
    """Fetch all pages"""
    results = []
    page = 1
    params = params or {}
    
    while True:
        params["_nPage"] = page
        r = session.get(url, params=params).json()
        records = r.get("_aRecords", [])
        results.extend(records)
        
        if r.get("_aMetadata", {}).get("_bIsComplete", True):
            break
        page += 1
    
    return results

# Usage
all_mods = fetch_all(f"{BASE_WEB}/Game/4254/Subfeed", {"_nPerpage": 50})
```

---

## Extract Data

```python
def get_items(response):
    """Safely extract records"""
    if isinstance(response, dict):
        return response.get("_aRecords", [])
    return []

def get_mods_data(mod_id):
    """Get key mod info"""
    data = get_mod(mod_id)
    return {
        "name": data.get("_sName"),
        "views": data.get("_nViewCount"),
        "downloads": data.get("_nDownloadCount"),
        "likes": data.get("_nLikeCount"),
        "files": data.get("_aFiles", []),
        "tags": data.get("_aTags", [])
    }
```

---

## Rate Limiter

```python
import time

class RateLimiter:
    def __init__(self, max_per_second=10):
        self.min_interval = 1.0 / max_per_second
        self.last_request = 0
    
    def wait(self):
        elapsed = time.time() - self.last_request
        if elapsed < self.min_interval:
            time.sleep(self.min_interval - elapsed)
        self.last_request = time.time()

limiter = RateLimiter(10)

# Use before each request
def safe_get(url, **kwargs):
    limiter.wait()
    return session.get(url, **kwargs)
```

---

## Error Handling

```python
def safe_request(url, **kwargs):
    try:
        r = session.get(url, timeout=10, **kwargs)
        r.raise_for_status()
        return r.json()
    except requests.exceptions.HTTPError as e:
        if e.response.status_code == 404:
            return None
        elif e.response.status_code == 429:
            print("Rate limited, waiting...")
            time.sleep(60)
            return safe_request(url, **kwargs)
        raise
    except requests.exceptions.RequestException as e:
        print(f"Error: {e}")
        return None
```

---

## Complete Example

```python
import requests

BASE = "https://gamebanana.com/apiv11"
session = requests.Session()
session.headers["User-Agent"] = "MyApp/1.0"

# Find mods for a game
game_id = 4254  # Counter-Strike 1.6
r = session.get(f"{BASE}/Game/{game_id}/Subfeed", params={"_nPerpage": 5})
data = r.json()

print(f"Found {data['_aMetadata']['_nRecordCount']} mods")
for mod in data["_aRecords"]:
    print(f"  - {mod['_sName']} ({mod.get('_nDownloadCount', 0)} downloads)")
```
