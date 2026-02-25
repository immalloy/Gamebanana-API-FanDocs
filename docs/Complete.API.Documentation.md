# GameBanana Complete API Documentation

## Overview

GameBanana has **two APIs**:

1. **Official API** (`api.gamebanana.com`) - Documented, rate-limited
2. **Web API** (`gamebanana.com/apiv11`) - Undocumented, used by the website (RECOMMENDED)

---

## Official API (api.gamebanana.com)

Base URL: `https://api.gamebanana.com`

### Endpoints (21 total)

| Category | Endpoint | Description |
|----------|----------|-------------|
| App | `/Core/App/Authenticate` | Authenticate app and get token |
| Item | `/Core/Item/Data` | Get item data by ID |
| Item | `/Core/Item/Data/AllowedItemTypes` | List allowed item types |
| Item | `/Core/Item/Data/AllowedFields` | List allowed fields for type |
| Item | `/Core/Item/IdentifyById` | Check if item exists |
| List | `/Core/List/Like` | Fuzzy search by field |
| List | `/Core/List/Like/AllowedItemTypes` | List allowed types for search |
| List | `/Core/List/Like/AllowedFields` | List allowed fields for search |
| List | `/Core/List/Section` | List items by section with filters |
| List | `/Core/List/Section/AllowedItemTypes` | List allowed types |
| List | `/Core/List/Section/AllowedSorts` | List sort options |
| List | `/Core/List/Section/AllowedFilters` | List filter options |
| List | `/Core/List/Section/AllowedFilterOperators` | List filter operators |
| List | `/Core/List/New` | List newest submissions |
| List | `/Core/List/New/AllowedItemTypes` | List allowed types |
| Member | `/Core/Member/Match` | Find users by username |
| Member | `/Core/Member/Identify` | Get user ID from username |
| Member | `/Core/Member/IdentifyById` | Get username from user ID |
| RSS | `/Rss/Featured` | Featured submissions RSS |
| RSS | `/Rss/Featured/AllowedItemTypes` | List allowed types |
| RSS | `/Rss/New` | New submissions RSS |
| RSS | `/Rss/New/AllowedItemTypes` | List allowed types |

### Response Formats

All endpoints support `format` parameter:
- `json` - Prettified JSON (default)
- `json_min` - Minified JSON
- `xml` - XML
- `php_serialized` - PHP serialized

### Limitations

- No direct category filtering for mods
- Only `userid` filter available for mods in Section endpoint

---

## Web API (apiv11) - RECOMMENDED

Base URL: `https://gamebanana.com/apiv11`

This is an undocumented internal API that provides **much richer data** than the official API.

### Profile Endpoints (Get item details)

| Endpoint | Description |
|----------|-------------|
| `/Member/{user_id}/ProfilePage` | Get member profile |
| `/Game/{game_id}/ProfilePage` | Get game profile (includes ALL categories!) |
| `/Mod/{mod_id}/ProfilePage` | Get mod profile |
| `/Studio/{studio_id}/ProfilePage` | Get studio profile |
| `/App/{app_id}/ProfilePage` | Get app profile |
| `/Bug/{bug_id}/ProfilePage` | Get bug report |
| `/Idea/{idea_id}/ProfilePage` | Get idea |
| `/Club/{club_id}/ProfilePage` | Get club |
| `/File/{file_id}` | Get file details + **archive file tree** |

### List/Search Endpoints

| Endpoint | Description |
|----------|-------------|
| `/Util/Search/Results` | Search with filters (INCLUDES CATEGORY INFO) |
| `/Member/Moderators` | List moderators with profiles |
| `/Member/Online` | Currently online members |
| `/Member/GameManagers` | List of game managers |
| `/Util/Generic/Discussions` | Recent discussions with submissions |

### Search Parameters

```
/Util/Search/Results?_sSearchString=query&_sModelName=Mod&_sOrder=date&_nPage=1&_nPerpage=15
```

| Parameter | Description |
|-----------|-------------|
| `_sSearchString` | Search query |
| `_sModelName` | Model type (Mod, Game, Member, etc.) |
| `_sOrder` | Sort order (date, relevance) |
| `_nPage` | Page number |
| `_nPerpage` | Results per page (max ~50) |
| `_csvFields` | Fields to return |

### Model Types (for search)

```
App, Article, ArticleCategory, Blog, BlogCategory, Bug, Club, Clan, 
Concept, ConceptCategory, Contest, ContestCategory, Event, EventCategory, 
Forum, Game, Generator, Idea, Jam, JamCategory, Member, Mod, ModCategory, 
News, NewsCategory, Poll, PollCategory, Project, Question, QuestionCategory, 
Request, RequestCategory, Script, ScriptCategory, Sound, SoundCategory, 
Spray, SprayCategory, Studio, Thread, Tool, ToolCategory, Tutorial, 
TutorialCategory, Wip, Ware
```

---

## Complete Examples

### Example 1: Get Mod Details

```bash
# Web API (recommended - more detail)
curl "https://gamebanana.com/apiv11/Mod/650004/ProfilePage"
```

Returns:
- `_sName` - Mod name
- `_aCategory` - Category info (id, name, url)
- `_aSuperCategory` - Parent category
- `_aGame` - Game info
- `_aFiles` - Array of files with download URLs
- `_aArchivedFiles` - Old versions
- `_nDownloadCount`, `_nLikeCount`, `_nViewCount` - Stats
- `_sDescription`, `_sText` - Description and full text
- `_aTags` - Tags array
- `_aRequirements` - Dependencies
- `_aEmbeddables` - Embed codes

### Example 2: Get Game with ALL Categories

```bash
# Get game with ALL its mod categories
curl "https://gamebanana.com/apiv11/Game/8694/ProfilePage"
```

Returns `_aModRootCategories` array:
```json
{
  "_aModRootCategories": [
    {"_idRow": 3827, "_sName": "Executables", "_nItemCount": 31938},
    {"_idRow": 3833, "_sName": "Skins", "_nItemCount": 24362},
    {"_idRow": 3819, "_sName": "New Songs", "_nItemCount": 14433},
    ...
  ]
}
```

Also returns `_aSections` with all content types:
- Blogs, Concepts, Contests, Events, Threads, Jams, News, Polls, Questions, Requests, Scripts, Sounds, Tools, Tutorials, Wares, WiPs

### Example 3: Search Mods (with category!)

```bash
# Search for mods - results INCLUDE category!
curl "https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=sonic&_sModelName=Mod&_nPage=1&_nPerpage=10"
```

Each result includes:
```json
{
  "_idRow": 650004,
  "_sName": "FNF: SONIC JAM!",
  "_aGame": {"_idRow": 8694, "_sName": "Friday Night Funkin'"},
  "_aRootCategory": {"_idRow": 29202, "_sName": "Base Game Mod Folders"},
  "_nLikeCount": 448,
  "_nDownloadCount": 52423
}
```

### Example 4: Get File Contents (Archive Tree)

```bash
# Get file details INCLUDING full archive file structure!
curl "https://gamebanana.com/apiv11/File/1634283"
```

Returns `_aArchiveFileTree` with complete file structure:
```json
{
  "_idRow": 1634283,
  "_sFile": "sonicjam_pc_.zip",
  "_nFilesize": 429069508,
  "_sMd5Checksum": "18ef3af677655355ce4ef206aa371ed7",
  "_sAnalysisResult": "ok",
  "_aArchiveFileTree": {
    "SonicJamX": {
      "data": {
        "characters": ["sonic.json", ...],
        "songs": {
          "bopeebo": ["bopeebo-metadata.json", ...],
          ...
        }
      },
      "images": { ... },
      "music": { ... },
      "scripts": { ... }
    }
  }
}
```

### Example 5: Get Member Profile

```bash
# Get full member profile
curl "https://gamebanana.com/apiv11/Member/1382/ProfilePage"
```

Returns:
- `_sName` - Username
- `_sAvatarUrl`, `_sHdAvatarUrl` - Avatar URLs
- `_nPoints`, `_nPointsRank` - Points rank
- `_nPostCount`, `_nSubscriberCount` - Activity stats
- `_aBio` - Profile bio fields
- `_aNormalMedals`, `_aRareMedals`, `_aLegendaryMedals` - All medals
- `_aBuddies` - Recent buddies
- `_aContactInfo` - Social links
- `_aPcSpecs` - PC specs
- `_aSoftwareKit` - Software used

### Example 6: List New Mods for Game

```bash
# Using official API
curl "https://api.gamebanana.com/Core/List/New?gameid=8694&itemtype=Mod&page=1"
```

### Example 7: Get Online Members

```bash
# Currently online members
curl "https://gamebanana.com/apiv11/Member/Online?_nPage=1&_nPerpage=10"
```

Returns member list with online status and current location.

### Example 8: Get Discussions

```bash
# Recent discussions across all content
curl "https://gamebanana.com/apiv11/Util/Generic/Discussions?_nPage=1&_nPerpage=5"
```

Returns submissions with their latest comments.

### Example 9: Get Game Managers

```bash
# List of game managers
curl "https://gamebanana.com/apiv11/Member/GameManagers?_nPage=1&_nPerpage=10"
```

### Example 10: Get Moderators

```bash
# Site moderators
curl "https://gamebanana.com/apiv11/Member/Moderators"
```

---

## Key Data Fields

### Mod Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `_idRow` | int | Mod ID |
| `_sName` | string | Mod name |
| `_sDescription` | string | Short description |
| `_sText` | string | Full description (HTML) |
| `_aCategory` | object | Category info |
| `_aSuperCategory` | object | Parent category |
| `_aGame` | object | Game info |
| `_aFiles` | array | Current files |
| `_aArchivedFiles` | array | Old file versions |
| `_nDownloadCount` | int | Total downloads |
| `_nLikeCount` | int | Total likes |
| `_nViewCount` | int | Total views |
| `_nPostCount` | int | Comment count |
| `_aTags` | array | Tags |
| `_aRequirements` | array | Game requirements |
| `_aSubmitter` | object | Author info |
| `_sVersion` | string | Current version |

### Game Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `_idRow` | int | Game ID |
| `_sName` | string | Game name |
| `_sAbbreviation` | string | Short name |
| `_nSubscriberCount` | int | Subscriber count |
| `_aModRootCategories` | array | All mod categories |
| `_aSections` | array | All content sections |
| `_aManagers` | array | Game managers |

### File Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `_idRow` | int | File ID |
| `_sFile` | string | Filename |
| `_nFilesize` | int | Size in bytes |
| `_sDownloadUrl` | string | Download URL |
| `_sMd5Checksum` | string | MD5 hash |
| `_sVersion` | string | File version |
| `_sDescription` | string | File description |
| `_sAnalysisResult` | string | Virus scan result |
| `_aArchiveFileTree` | object | Full file structure! |

### Member Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `_idRow` | int | User ID |
| `_sName` | string | Username |
| `_sAvatarUrl` | string | Avatar URL |
| `_nPoints` | int | Points |
| `_nPointsRank` | int | Rank |
| `_nPostCount` | int | Post count |
| `_aBio` | array | Bio fields |
| `_aMedals` | array | Medals earned |
| `_aBuddies` | array | Friends list |

---

## Response Key Prefixes

Web API responses use these prefixes:

| Prefix | Type |
|--------|------|
| `_idRow` | ID |
| `_sName` | String |
| `_nXxx` | Number |
| `_bXxx` | Boolean |
| `_aXxx` | Array/Object |
| `_tsXxx` | Timestamp |

---

## Libraries

| Language | Library | Uses |
|----------|---------|------|
| Python | [pybanana](https://github.com/gamebanana/pybanana) | Web API (apiv11) |
| Deno/TS | [gamebanana](https://deno.land/x/gamebanana) | Official API |

---

## Important Notes

1. **No authentication required** for read operations on Web API
2. **Categories are per-game** - use Game ProfilePage to get all categories
3. **Search results include category info** - `_aRootCategory` field
4. **File endpoint reveals full archive structure** - `_aArchiveFileTree`
5. **No official rate limits** but be respectful
6. **Use client-side filtering** for category filtering (no server-side filter by category)
