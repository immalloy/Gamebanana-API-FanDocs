# GameBanana API - Quick Start Guide

> Get up and running in 5 minutes

---

## Choose Your API

| Use Case | Recommended API |
|----------|----------------|
| Basic data access | Web API (apiv11) |
| Need official docs | Official API |
| Need ZIP file tree | Web API |
| Need authentication | Either |
| Simple lists | Either |

---

## Web API (apiv11) - Quick Start

### 1. Test the API

```bash
# Simple health check - search for something
curl "https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=test&_sModelName=Mod&_nPerpage=1"
```

### 2. Find a Game ID

Search games by name:
```bash
curl "https://gamebanana.com/apiv11/Util/Game/NameMatch?_sName=counter-strike"
```

### 3. Get Mods for a Game

```bash
# Replace 4254 with your game ID
curl "https://gamebanana.com/apiv11/Game/4254/Subfeed?_nPerpage=5"
```

### 4. Get Mod Details

```bash
# Replace with actual mod ID
curl "https://gamebanana.com/apiv11/Mod/650004/ProfilePage"
```

---

## Official API - Quick Start

### 1. Get Item Data

```bash
# Get mod details
curl "https://api.gamebanana.com/Core/Item/Data?itemtype=Mod&itemid=650004&format=json"
```

### 2. List New Items

```bash
# Latest mods
curl "https://api.gamebanana.com/Core/List/New?itemtype=Mod&format=json"
```

### 3. Search Users

```bash
curl "https://api.gamebanana.com/Core/Member/Match?name=username&format=json"
```

---

## Common Tasks in 3 Lines

### Search
```python
requests.get("https://gamebanana.com/apiv11/Util/Search/Results", 
             params={"_sSearchString": "map", "_sModelName": "Mod"})
```

### Get Game Categories
```python
requests.get("https://gamebanana.com/apiv11/Game/8694/ProfilePage")
# Returns _aModRootCategories with all category IDs!
```

### Get Files
```python
requests.get("https://gamebanana.com/apiv11/Mod/650004/DownloadPage")
```

### Get ZIP Contents
```python
# Only works with Web API!
requests.get("https://gamebanana.com/apiv11/File/FILE_ID")
# Returns _aArchiveFileTree with full ZIP structure
```

---

## Important Notes

### 1. Pagination
Check `_aMetadata._bIsComplete` - if `false`, more pages exist.

### 2. Rate Limits
- Be respectful
- Add delays between requests
- Cache responses when possible

### 3. Response Format
All responses are JSON with this structure:
```json
{
  "_aMetadata": { ... },
  "_aRecords": [ ... ]
}
```

### 4. Field Prefixes
Remember: `_s` = string, `_n` = number, `_a` = array, `_b` = boolean, `_ts` = timestamp

---

## Next Steps

- See [Use Cases](./Use.Cases.md) for more examples
- See [Field Reference](./Field.Reference.md) for all fields
- See [Error Codes](./Error.Codes.md) for error handling
