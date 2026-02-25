# GameBanana Web API (apiv11)

This is an undocumented internal API that provides more detailed data than the official `api.gamebanana.com`.

**Base URL:** `https://gamebanana.com/apiv11`

## Endpoints

### Member Profile

**Get member profile by ID**
```
GET https://gamebanana.com/apiv11/Member/{user_id}/ProfilePage
```

**Example:** `https://gamebanana.com/apiv11/Member/1382/ProfilePage`

Returns detailed profile including:
- Name, avatar, user title
- Points, post count, subscriber count
- Online status
- Medals (normal, rare, legendary)
- Bio information
- PC specs
- Software kit
- Gaming devices
- Recent buddies

---

### Mod Profile

**Get mod profile by ID**
```
GET https://gamebanana.com/apiv11/Mod/{mod_id}/ProfilePage
```

**Example:** `https://gamebanana.com/apiv11/Mod/650004/ProfilePage`

Returns detailed mod info including:
- Name, description
- Category (`_aCategory`) and supercategory (`_aSuperCategory`)
- Game info (`_aGame`)
- Files (`_aFiles`) with download URLs, versions, MD5 checksums
- Preview images
- Like count, view count, download count
- Submitter info
- Credits
- Requirements
- Alternate file sources

---

### Game Profile

**Get game profile by ID**
```
GET https://gamebanana.com/apiv11/Game/{game_id}/ProfilePage
```

---

### Studio Profile

**Get studio profile by ID**
```
GET https://gamebanana.com/apiv11/Studio/{studio_id}/ProfilePage
```

---

### App Profile

**Get app profile by ID**
```
GET https://gamebanana.com/apiv11/App/{app_id}/ProfilePage
```

---

### Bug Report

**Get bug report by ID**
```
GET https://gamebanana.com/apiv11/Bug/{bug_id}/ProfilePage
```

---

### Idea

**Get idea by ID**
```
GET https://gamebanana.com/apiv11/Idea/{idea_id}/ProfilePage
```

---

### Club

**Get club by ID**
```
GET https://gamebanana.com/apiv11/Club/{club_id}/ProfilePage
```

---

## Search

**Search for content**
```
GET https://gamebanana.com/apiv11/Util/Search/Results
```

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `_sSearchString` | Search query |
| `_sModelName` | Model type (Mod, Game, Member, etc.) |
| `_sOrder` | Sort order |
| `_nPage` | Page number |
| `_nPerpage` | Results per page |
| `_csvFields` | Fields to return |

---

## Other Endpoints

| Endpoint | Description |
|----------|-------------|
| `/Member/Moderators` | List of moderators |
| `/Member/GameManagers` | List of game managers |
| `/Member/Online` | Currently online members |
| `/Util/Generic/Discussions` | Recent discussions |

---

## Response Format

All responses are JSON with keys prefixed with underscore:
- `_idRow` - Row ID
- `_sName` - String name
- `_aXxx` - Array/object data
- `_nXxx` - Numeric data
- `_bXxx` - Boolean data
- `_tsXxx` - Timestamp
