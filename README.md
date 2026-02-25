# GameBanana API Documentation

> **Offline documentation mirror** for GameBanana APIs - easy to read and reference

## Two APIs Available

GameBanana provides **two APIs**:

| API | Base URL | Documentation | Endpoints |
|-----|----------|---------------|-----------|
| **Official API** | `api.gamebanana.com` | [api.gamebanana.com](https://api.gamebanana.com/) | 21 |
| **Web API (v11)** | `gamebanana.com/apiv11` | This documentation | 104+ |

This repository contains comprehensive documentation for both APIs, with the Web API documentation being the most complete.

---

## Documentation Structure

```
Gamebanana API/
├── docs/
│   ├── official/                   # Official API endpoints (22)
│   │   ├── Core.App.Authenticate.md
│   │   ├── Core.Item.Data.md
│   │   ├── Core.List.Section.md
│   │   └── ...
│   ├── web/                       # Web API v11 endpoints (104+)
│   │   ├── search/                # Search & discovery
│   │   ├── games-*/               # Games related
│   │   ├── work-in-progress-*/    # WIP endpoints
│   │   ├── authentication-*/     # Auth endpoints
│   │   ├── submission-base-*/      # Base submission endpoints
│   │   └── ...
│   ├── Complete.API.Documentation.md
│   │   └── WebAPI.Complete.md         # All-in-one reference
│   ├── INDEX.md                       # All 126 endpoints
│   ├── Quick.Start.md                 # Get started (5 min)
│   ├── Use.Cases.md                  # 11 practical tutorials
│   ├── Field.Reference.md            # Response fields
│   ├── Error.Codes.md                # Error codes
│   ├── Best.Practices.md              # Rate limiting, caching
│   ├── Troubleshooting.md             # Common problems
│   ├── Python.Quickstart.md          # Python code snippets
│   ├── JavaScript.Quickstart.md      # JS/TS code snippets
│   └── openapi.yaml                  # OpenAPI spec
├── docs.json                      # Full index (138 entries)
├── SUMMARY.md                     # Organized index
└── README.md
```

---

## Quick Examples

### Web API (apiv11) - Recommended

```bash
# Get mod details
GET https://gamebanana.com/apiv11/Mod/650004/ProfilePage

# Search mods
GET https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=sonic&_sModelName=Mod

# Get game categories
GET https://gamebanana.com/apiv11/Game/8694/ProfilePage

# Get member profile
GET https://gamebanana.com/apiv11/Member/1382/ProfilePage
```

### Official API

```bash
# Get item data
GET https://api.gamebanana.com/Core/Item/Data?itemtype=Mod&itemid=650004

# List new submissions
GET https://api.gamebanana.com/Core/List/New?itemtype=Mod

# Search users
GET https://api.gamebanana.com/Core/Member/Match?name=user
```

---

## Key Differences

| Feature | Official API | Web API (v11) |
|---------|--------------|----------------|
| Documentation | Official | Unofficial (Postman) |
| File trees | No | Yes (`_aArchiveFileTree`) |
| Category info in search | No | Yes (`_aRootCategory`) |
| Authentication | Yes | Yes |
| Rate limits | Unknown | Respect robots.txt |

---

## Endpoints Overview

### Web API v11 (104 endpoints)

- **Search & Discovery** (11): Search, suggestions, tags, latest, featured
- **Games** (13): Search games, game info, submissions, top games
- **Work in Progress** (16): Categories, discussions, member content
- **Authentication** (3): Username & email auth
- **Submission Base** (34): Properties, files, likes, comments, subscriptions
- **Submission Types** (10): App, Contest, Collection, Idea, Jam, Poll, Project, Request
- **Ripe** (2): Ripe.info, purchasers
- **Dictionaries** (1): Trash reasons

### Official API (21 endpoints)

- Core/App (1): Authenticate
- Core/Item (4): Data, IdentifyById, AllowedItemTypes, AllowedFields
- Core/List (9): Like, New, Section + sub-endpoints
- Core/Member (3): Match, Identify, IdentifyById
- RSS (4): Featured, New + sub-endpoints

---

## Response Field Prefixes

GameBanana APIs use consistent prefixes:

| Prefix | Type |
|--------|------|
| `_a` | Array |
| `_b` | Boolean |
| `_idRow` | Database ID |
| `_n` | Number |
| `_s` | String |
| `_ts` | Timestamp |
| `_h` | Height (pixels) |
| `_w` | Width (pixels) |

---

## Credits

- **GameBanana** - For the amazing modding platform
- **Postman Collection** (`gb-api-v11`) - Community-contributed API documentation
- **pybanana** - Python library that helped discover the Web API
- **gamebanana (Deno)** - TypeScript library for the Official API

---

## Sources

- Official API docs: https://api.gamebanana.com/
- Web API Base: https://gamebanana.com/apiv11
- Postman Collection: `gb-api-v11` (104 endpoints)

---

## Crawl Date

February 25, 2026
