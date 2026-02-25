# GameBanana API - Complete Endpoint Index

> **126 endpoints** - Quick reference for all API endpoints
> 
> - **Web API (apiv11)**: 104 endpoints → `https://gamebanana.com/apiv11`
> - **Official API**: 22 endpoints → `https://api.gamebanana.com`

---

## Quick Lookup

### 🔍 Search & Discovery

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/Util/Search/Results`](web/search/Util.Search.Results.md) | GET | Search submissions |
| [`/Util/Search/Suggestions`](web/search/Util.Search.Suggestions.md) | GET | Search suggestions |
| [`/Util/Generic/Tags`](web/search/Util.Generic.Tags.md) | GET | Search tags |
| [`/Util/Game/NameMatch`](web/search/Util.Game.NameMatch.md) | GET | Search games by name |
| [`/:model_name/Index`](web/search/model_name.Index.md) | GET | List latest in section |
| [`/:model_name/ListFilterConfig`](web/search/model_name.ListFilterConfig.md) | GET | Get sort/filter options |
| [`/Util/Homepage/Submissions`](web/search/Util.Homepage.Submissions.md) | GET | Latest all games |
| [`/Util/List/Featured`](web/search/Util.List.Featured.md) | GET | Featured submissions |
| [`/Member/:id/SubFeed`](web/search/Member.id.SubFeed.md) | GET | Member's submissions |

### 🎮 Games

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/Game/:id/ProfilePage`](web/games-info-for-the-specified-game/Game.id.ProfilePage.md) | GET | Full game details + categories |
| [`/Game/:id`](web/games-info-for-the-specified-game/Game.id.md) | GET | Basic game info |
| [`/Game/:id/Subfeed`](web/games-search-submissions-for-the-specified-game/Game.id.Subfeed.md) | GET | Game's submissions |
| [`/Game/:id/TopSubs`](web/games-search-submissions-for-the-specified-game/Game.id.TopSubs.md) | GET | Top submissions |
| [`/Game/:id/CommunitySpotlight`](web/games-search-submissions-for-the-specified-game/Game.id.CommunitySpotlight.md) | GET | Community spotlight |
| [`/Game/Index`](web/games-search-games/Game.Index.md) | GET | List games |
| [`/Game/ListFilterConfig`](web/games-search-games/Game.ListFilterConfig.md) | GET | Game filter options |
| [`/Util/Homepage/TopGames`](web/games-search-games/Util.Homepage.TopGames.md) | GET | Trending/classic games |

### 👤 Members

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/Member/:id/ProfilePage`](web/work-in-progress-member/) | GET | Member profile |
| [`/Member/:id/SubFeed`](web/search/Member.id.SubFeed.md) | GET | Member's submissions |
| [`/Member/:id/LikedSubmissions`](web/work-in-progress-member/Member.id.LikedSubmissions.md) | GET | What member liked |
| [`/Member/:id/Medals`](web/work-in-progress-member/Member.id.Medals.md) | GET | Member's medals |
| [`/Member/:id/Submissions/Contributions`](web/work-in-progress-member/Member.id.Submissions.Contributions.md) | GET | Member's contributions |

### 📦 Submissions (Mods, Tools, etc.)

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/:section/:id/ProfilePage`](web/submission-base-properties/section_slug.submission_id.ProfilePage.md) | GET | Full submission details |
| [`/:section/:id`](web/submission-base-properties/section_slug.submission_id.md) | GET | Basic submission info |
| [`/:section/:id/DownloadPage`](web/submission-base-files/section_slug.submission_id.DownloadPage.md) | GET | Download info + files |
| [`/File/:id`](web/submission-base-files/File.file_id.md) | GET | **ZIP file tree!** |
| [`/:section/:id/Likes`](web/submission-base-likes/section_slug.submission_id.Likes.md) | GET | Who liked |
| [`/:section/:id/Posts`](web/submission-base-posts-replies/section_slug.submission_id.Posts.md) | GET | Comments |
| [`/:section/:id/Updates`](web/submission-base-updates/section_slug.submission_id.Updates.md) | GET | Changelogs |
| [`/:section/:id/Subscribers`](web/submission-base-subscription/section_slug.submission_id.Subscribers.md) | GET | Subscribers |
| [`/:section/:id/Collections`](web/submission-base-collections/section_slug.submission_id.Collections.md) | GET | Collections |

### 🔐 Authentication

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/Member/Authenticate`](web/authentication-via-username/Member.Authenticate.md) | POST | Login with username |
| [`/Member/EmailAuthenticate`](web/authentication-via-email/Member.EmailAuthenticate.md) | POST | Login with email |
| [`/:section/:id/Like`](web/submission-base-likes/section_slug.submission_id.Like.md) | POST | Like (auth required) |
| [`/:section/:id/Subscription/Add`](web/submission-base-subscription/section_slug.submission_id.Subscription.Add.md) | POST | Subscribe (auth) |
| [`/:section/:id/Thank/Add`](web/submission-base-thanks/section_slug.submission_id.Thank.Add.md) | POST | Thank (auth) |

### 📝 Submission Types Specific

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/App/:id/Users`](web/submission-app/App.submission_id.Users.md) | GET | App users |
| [`/Contest/:id/Winners`](web/submission-contest/Contest.submission_id.Winners.md) | GET | Contest winners |
| [`/Collection/:id/Items`](web/submission-collection/Collection.submission_id.Items.md) | GET | Collection items |
| [`/Idea/:id/Ratings`](web/submission-idea/Idea.submission_id.Ratings.md) | GET | Idea ratings |
| [`/Jam/:id/Entries`](web/submission-jam/Jam.submission_id.Entries.md) | GET | Jam entries |
| [`/Poll/:id/Votes`](web/submission-poll/Poll.submission_id.Votes.md) | GET | Poll votes |
| [`/Project/:id/Wips`](web/submission-project/Project.submission_id.Wips.md) | GET | Project WIPs |

### 🔧 Other

| Endpoint | Method | Description |
|----------|--------|-------------|
| [`/Util/Config/TrashReasons`](web/dictionaries/Util.Config.TrashReasons.md) | GET | Delete reasons |
| [`/Ripe/Info`](web/ripe/Ripe.Info.md) | GET | Ripe.info stats |
| [`/Ripe/Purchasers`](web/ripe/Ripe.Purchasers.md) | GET | Latest purchasers |

---

## Official API Endpoints

Base URL: `https://api.gamebanana.com`

### Core

| Endpoint | Description |
|----------|-------------|
| `/Core/App/Authenticate` | Authenticate app |
| `/Core/Item/Data` | Get item data |
| `/Core/Item/IdentifyById` | Verify item exists |
| `/Core/List/New` | List new items |
| `/Core/List/Section` | List by section |
| `/Core/List/Like` | List liked items |
| `/Core/Member/Match` | Search members |
| `/Core/Member/Identify` | Get member ID by name |
| `/Core/Member/IdentifyById` | Get member name by ID |

### RSS

| Endpoint | Description |
|----------|-------------|
| `/Rss/Featured` | Featured items RSS |
| `/Rss/New` | New items RSS |

---

## Common Parameters

### Pagination

| Parameter | Values | Default | Description |
|-----------|--------|---------|-------------|
| `_nPage` | 1+ | 1 | Page number |
| `_nPerpage` | 1-50 | 20 | Results per page |

### Sorting

| Parameter | Values | Description |
|-----------|--------|-------------|
| `_sOrder` | `best_match`, `popularity`, `date`, `udate` | Search sort |
| `_sSort` | `default`, `new`, `updated` | List sort |

### Filtering

| Parameter | Values | Description |
|-----------|--------|-------------|
| `_sModelName` | Mod, Game, Tool, etc. | Section type |
| `_idGameRow` | Game ID | Filter by game |
| `_csvModelInclusions` | Comma-list | Include sections |
| `_csvTagInclusions` | Tag IDs | Include by tags |

---

## Response Quick Ref

```json
{
  "_aMetadata": {
    "_nRecordCount": 100,
    "_bIsComplete": false
  },
  "_aRecords": [
    {
      "_idRow": 123,
      "_sName": "Item Name",
      "_sModelName": "Mod"
    }
  ]
}
```

**Metadata**: `_aMetadata._bIsComplete` = `false` means more pages!

---

## Quick Examples

### Search Mods
```bash
curl "https://gamebanana.com/apiv11/Util/Search/Results?_sSearchString=sonic&_sModelName=Mod"
```

### Get Game Categories
```bash
curl "https://gamebanana.com/apiv11/Game/8694/ProfilePage"
# Returns _aModRootCategories!
```

### Get Mod Files
```bash
curl "https://gamebanana.com/apiv11/Mod/650004/DownloadPage"
```

### Get ZIP Contents
```bash
curl "https://gamebanana.com/apiv11/File/FILE_ID"
# Returns _aArchiveFileTree!
```

---

*Last updated: February 2026*
