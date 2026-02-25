# GameBanana API - Use Cases & Tutorials

> Practical examples for common tasks using the Web API (apiv11)

---

## Prerequisites

Base URL: `https://gamebanana.com/apiv11`

All examples use `GET` requests unless otherwise noted.

---

## 1. Search for Mods

### Basic Search

```bash
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=sonic&_sModelName=Mod
```

### Search Within a Game

```bash
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=map&_sModelName=Mod&idGameRow=4254
```

### Search with Sorting

```bash
# Most popular first
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=weapon&_sModelName=Mod&_sOrder=popularity

# Newest first
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=weapon&_sModelName=Mod&_sOrder=date

# Recently updated
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=weapon&_sModelName=Mod&_sOrder=udate
```

---

## 2. Get Game Information

### Get Game Profile with Categories

```bash
GET https://gamebanana.com/apiv11/Game/8694/ProfilePage
```

**Returns:** Game name, description, icon, banner, and ALL category IDs in `_aModRootCategories`

### Get Game Submissions

```bash
# Latest submissions
GET https://gamebanana.com/apiv11/Game/4254/Subfeed?_nPage=1&_sSort=default

# Top submissions (day/week/month/year/all)
GET https://gamebanana.com/apiv11/Game/4254/TopSubs?period=month
```

### Search Games by Name

```bash
GET https://gamebanana.com/apiv11/Util/Game/NameMatch?_sName=halo
```

---

## 3. Get Mod/Submission Details

### Get Full Submission Data

```bash
GET https://gamebanana.com/apiv11/Mod/650004/ProfilePage
```

**Returns:** Full submission data including:
- Name, description, tags
- Download count, like count
- Files list
- Category info
- Submitter info
- Preview images

### Get Submission Files

```bash
# Option 1: Inline in ProfilePage
GET https://gamebanana.com/apiv11/Mod/650004/ProfilePage

# Option 2: Download page
GET https://gamebanana.com/apiv11/Mod/650004/DownloadPage

# Option 3: Get specific file contents
GET https://gamebanana.com/apiv11/File/123456
```

### Get ZIP Archive Tree (Unique to Web API!)

```bash
GET https://gamebanana.com/apiv11/File/123456
```

Returns `_aArchiveFileTree` with full ZIP structure - lists ALL files inside!

---

## 4. Get Member Information

### Get Member Profile

```bash
GET https://gamebanana.com/apiv11/Member/1382/ProfilePage
```

### Get Member's Submissions

```bash
GET https://gamebanana.com/apiv11/Member/1382/SubFeed
```

### Get Member's Liked Submissions

```bash
GET https://gamebanana.com/apiv11/Member/1382/LikedSubmissions
```

### Get Member's Medals

```bash
GET https://gamebanana.com/apiv11/Member/1382/Medals
```

---

## 5. Interacting with Submissions

### Get Like Count

```bash
GET https://gamebanana.com/apiv11/Mod/650004
# Returns _nLikeCount in response
```

### Get Who Liked

```bash
GET https://gamebanana.com/apiv11/Mod/650004/Likes
```

### Get Comments/Posts

```bash
GET https://gamebanana.com/apiv11/Mod/650004/Posts
```

### Get Updates/Changelogs

```bash
GET https://gamebanana.com/apiv11/Mod/650004/Updates
```

---

## 6. Browse by Section

### Latest in Section

```bash
# Latest mods
GET https://gamebanana.com/apiv11/Mod/Index?_nPage=1&_nPerpage=20

# Latest tools
GET https://gamebanana.com/apiv11/Tool/Index?_nPage=1&_nPerpage=20
```

### Featured Only

```bash
GET https://gamebanana.com/apiv11/Util/List/Featured?_sModelName=Mod
```

### Get Section Filters/Sorts

```bash
GET https://gamebanana.com/apiv11/Mod/ListFilterConfig
```

Returns available sort options and filters for that section.

---

## 7. Get Tags

### Search Tags

```bash
GET https://gamebanana.com/apiv11/Util/Generic/Tags?_sTag=realistic
```

### Tags for Specific Game

```bash
GET https://gamebanana.com/apiv11/Util/Generic/Tags?_sTag=weapon&_idGameRow=4254
```

---

## 8. Pagination

### Checking for More Pages

Every response includes `_aMetadata`:

```json
{
  "_aMetadata": {
    "_nRecordCount": 285,
    "_bIsComplete": false
  }
}
```

- `_bIsComplete: false` = more pages available
- `_bIsComplete: true` = last page

### Paginated Request

```bash
# Page 1
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=map&_nPage=1&_nPerpage=20

# Page 2
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=map&_nPage=2&_nPerpage=20
```

---

## 9. Authentication (POST)

### Login with Username

```bash
POST https://gamebanana.com/apiv11/Member/Authenticate

Body (x-www-form-urlencoded):
  _sName=username
  _sPassword=password
```

### Login with Email

```bash
# Step 1: Request code
POST https://gamebanana.com/apiv11/Member/EmailAuthenticate
Body:
  _sEmail=user@example.com

# Step 2: Submit code
POST https://gamebanana.com/apiv11/Member/EmailAuthenticate
Body:
  _sEmail=user@example.com
  _sCode=123456
```

---

## 10. Complete Python Example

```python
import requests

BASE = "https://gamebanana.com/apiv11"

def search_mods(query, game_id=None, page=1, perpage=20):
    """Search for mods"""
    params = {
        "_sSearchString": query,
        "_sModelName": "Mod",
        "_nPage": page,
        "_nPerpage": perpage
    }
    if game_id:
        params["_idGameRow"] = game_id
    
    r = requests.get(f"{BASE}/Util/Search/Results", params=params)
    return r.json()

def get_mod(mod_id):
    """Get full mod details"""
    r = requests.get(f"{BASE}/Mod/{mod_id}/ProfilePage")
    return r.json()

def get_game_with_categories(game_id):
    """Get game info including ALL categories"""
    r = requests.get(f"{BASE}/Game/{game_id}/ProfilePage")
    data = r.json()
    return {
        "name": data.get("_sName"),
        "categories": data.get("_aModRootCategories", []),
        "description": data.get("_sDescription")
    }

# Example usage
mods = search_mods("weapon", game_id=4254)
print(f"Found {mods['_aMetadata']['_nRecordCount']} mods")

game = get_game_with_categories(8694)
print(f"Game: {game['name']}")
print(f"Categories: {len(game['categories'])}")
```

---

## 11. Response Parsing Tips

### Extract Items from Response

```python
def get_items(response):
    """Safely extract records from response"""
    if isinstance(response, dict):
        return response.get("_aRecords", [])
    return []

# Usage
data = search_mods("map")
items = get_items(data)
for item in items:
    print(item["_sName"], item.get("_nDownloadCount", 0))
```

### Check Pagination

```python
def has_more_pages(response):
    """Check if more pages available"""
    meta = response.get("_aMetadata", {})
    return not meta.get("_bIsComplete", True)
```
