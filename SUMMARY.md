# GameBanana API Documentation - Summary

> **Complete API Reference** - 104+ endpoints documented from Postman Collection

---

## Table of Contents

- [Overview](#overview)
- [Web API v11 (apiv11)](#web-api-v11-apiv11)
  - [Search & Discovery](#search--discovery)
  - [Games](#games)
  - [Work in Progress](#work-in-progress)
  - [Authentication](#authentication)
  - [Submission - Base](#submission---base)
  - [Submission - Specific Types](#submission---specific-types)
  - [Ripe](#ripe)
  - [Dictionaries](#dictionaries)
- [Official API](#official-api)

---

## Overview

| Document | Description |
|----------|-------------|
| [Complete API Documentation](./docs/Complete.API.Documentation.md) | Full documentation for both APIs |
| [Web API Complete Reference](./docs/WebAPI.Complete.md) | All 104 endpoints in single file |

---

## Guides

| Document | Description |
|----------|-------------|
| [Quick Start Guide](./docs/Quick.Start.md) | Get started in 5 minutes |
| [Use Cases & Tutorials](./docs/Use.Cases.md) | Practical examples for common tasks |
| [Best Practices](./docs/Best.Practices.md) | Rate limiting, caching, error handling |
| [Troubleshooting Guide](./docs/Troubleshooting.md) | Common problems and solutions |

---

## Reference

| Document | Description |
|----------|-------------|
| [Complete Endpoint Index](./docs/INDEX.md) | All 126 endpoints quick lookup |
| [Response Field Reference](./docs/Field.Reference.md) | All response field prefixes |
| [Error Codes Reference](./docs/Error.Codes.md) | All error codes |
| [OpenAPI Spec](./docs/openapi.yaml) | Machine-readable API spec |

---

## Code Examples

| Document | Description |
|----------|-------------|
| [Python Quick Reference](./docs/Python.Quickstart.md) | Copy-paste Python code |
| [JavaScript Quick Reference](./docs/JavaScript.Quickstart.md) | Copy-paste JS/TS code |

---

## Web API v11 (apiv11)

Base URL: `https://gamebanana.com/apiv11`

### Search & Discovery

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/Util/Search/Results](./docs/web/search/Util.Search.Results.md) | GET | Advanced search |
| [/:model_name/ListFilterConfig](./docs/web/search/model_name.ListFilterConfig.md) | GET | Search modificators |
| [/Util/Search/Suggestions](./docs/web/search/Util.Search.Suggestions.md) | GET | Search suggestions |
| [/Util/Game/NameMatch](./docs/web/search/Util.Game.NameMatch.md) | GET | Games by name |
| [/Util/Generic/Tags](./docs/web/search/Util.Generic.Tags.md) | GET | Tags by text |
| [/Util/Homepage/Submissions](./docs/web/search/Util.Homepage.Submissions.md) | GET | Latest (all games) |
| [/Game/:id/Subfeed](./docs/web/search/Game.id.Subfeed.md) | GET | Latest (game) |
| [/:model_name/Index](./docs/web/search/model_name.Index.md) | GET | Latest (section) |
| [/Member/:id/SubFeed](./docs/web/search/Member.id.SubFeed.md) | GET | Latest (member) |
| [/Util/List/Featured](./docs/web/search/Util.List.Featured.md) | GET | Featured |
| [/Game/:id/TopSubs](./docs/web/search/Game.id.TopSubs.md) | GET | Top (game) |

### Games

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/Game/:id/ProfilePage](./docs/web/games-info-for-the-specified-game/Game.id.ProfilePage.md) | GET | Multiple Properties (1) |
| [/Game/:id](./docs/web/games-info-for-the-specified-game/Game.id.md) | GET | Multiple Properties (2) |
| [/Game/:id/GetStartedPage](./docs/web/games-info-for-the-specified-game/Game.id.GetStartedPage.md) | GET | Detailed information |
| [/Game/:id/Rules](./docs/web/games-info-for-the-specified-game/Game.id.Rules.md) | GET | Additional rules |
| [/Util/Generic/Discussions](./docs/web/games-misc/Util.Generic.Discussions.md) | GET | Discussions |
| [/Util/Homepage/TopGames](./docs/web/games-search-games/Util.Homepage.TopGames.md) | GET | Trending, Classics, New |
| [/Util/Game/NameMatch](./docs/web/games-search-games/Util.Game.NameMatch.md) | GET | By name |
| [/Game/ListFilterConfig](./docs/web/games-search-games/Game.ListFilterConfig.md) | GET | Sort options and filters |
| [/Game/Index](./docs/web/games-search-games/Game.Index.md) | GET | By sort options and filters |
| [/Game/:id/TopSubs](./docs/web/games-search-submissions-for-the-specified-game/Game.id.TopSubs.md) | GET | Top submissions |
| [/Util/List/Featured](./docs/web/games-search-submissions-for-the-specified-game/Util.List.Featured.md) | GET | Featured |
| [/Game/:id/CommunitySpotlight](./docs/web/games-search-submissions-for-the-specified-game/Game.id.CommunitySpotlight.md) | GET | Community Spotlight |
| [/Game/:id/Subfeed](./docs/web/games-search-submissions-for-the-specified-game/Game.id.Subfeed.md) | GET | Advanced search |

### Work in Progress

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/:sectionSlug/Categories](./docs/web/work-in-progress-categories/sectionSlug.Categories.md) | GET | Multiple RootCategories |
| [/ModCategory/:rootCategoryId/SubCategories](./docs/web/work-in-progress-categories/ModCategory.rootCategoryId.SubCategories.md) | GET | Multiple SubCategories |
| [/Util/Generic/Discussions](./docs/web/work-in-progress-discussions/Util.Generic.Discussions.md) | GET | Multiple Discussions |
| [/Util/Homepage/Features](./docs/web/work-in-progress-homepage/Util.Homepage.Features.md) | GET | Features |
| [/Util/Homepage/CommunitySpotlight](./docs/web/work-in-progress-homepage/Util.Homepage.CommunitySpotlight.md) | GET | CommunitySpotlight |
| [/Member/:id/AwardedBounties](./docs/web/work-in-progress-member/Member.id.AwardedBounties.md) | GET | Awarded Bounties |
| [/Member/:id/ContributedBounties](./docs/web/work-in-progress-member/Member.id.ContributedBounties.md) | GET | Contributed Bounties |
| [/Member/:id/LikedSubmissions](./docs/web/work-in-progress-member/Member.id.LikedSubmissions.md) | GET | Liked Submissions |
| [/Member/:id/Medals](./docs/web/work-in-progress-member/Member.id.Medals.md) | GET | Medals |
| [/Member/:id/ParticipatedContests](./docs/web/work-in-progress-member/Member.id.ParticipatedContests.md) | GET | Participated Contests |
| [/Member/:id/RatedIdeas](./docs/web/work-in-progress-member/Member.id.RatedIdeas.md) | GET | Rated Ideas |
| [/Member/:id/SolvedQuestions](./docs/web/work-in-progress-member/Member.id.SolvedQuestions.md) | GET | Solved Questions |
| [/Member/:id/ThankedSubmissions](./docs/web/work-in-progress-member/Member.id.ThankedSubmissions.md) | GET | Thanked Submissions |
| [/Member/:id/VotedPolls](./docs/web/work-in-progress-member/Member.id.VotedPolls.md) | GET | Voted Polls |
| [/Member/:id/Submissions/Contributions](./docs/web/work-in-progress-member/Member.id.Submissions.Contributions.md) | GET | Contributions |
| [/Member/:id/Submissions/Posts](./docs/web/work-in-progress-member/Member.id.Submissions.Posts.md) | GET | Latest Posts |

### Authentication

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/Member/EmailAuthenticate](./docs/web/authentication-via-email/Member.EmailAuthenticate.md) | POST | 1. Request confirmation code |
| [/Member/EmailAuthenticate](./docs/web/authentication-via-email/Member.EmailAuthenticate.md) | POST | 2. Submit confirmation code |
| [/Member/Authenticate](./docs/web/authentication-via-username/Member.Authenticate.md) | POST | Authenticate |

### Submission - Base

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/:section_slug/:submission_id/Collections](./docs/web/submission-base-collections/section_slug.submission_id.Collections.md) | GET | Collections added to |
| [/:section_slug/:submission_id/AccessorCollections](./docs/web/submission-base-collections/section_slug.submission_id.AccessorCollections.md) | GET | Accessor collections |
| [/Collection/Add](./docs/web/submission-base-collections/Collection.Add.md) | POST | [Auth] Create a Collection |
| [/:section_slug/:submission_id/AddToCollection](./docs/web/submission-base-collections/section_slug.submission_id.AddToCollection.md) | POST | [Auth] Add to Collection |
| [/:section_slug/:submission_id/RemoveFromCollection](./docs/web/submission-base-collections/section_slug.submission_id.RemoveFromCollection.md) | DELETE | [Auth] Remove from Collection |
| [/:section_slug/:submission_id/EmbeddablesPage](./docs/web/submission-base-embeds/section_slug.submission_id.EmbeddablesPage.md) | GET | Embeds list |
| [/:section_slug/:submission_id](./docs/web/submission-base-files/section_slug.submission_id.md) | GET | Files list (Option 1) |
| [/:section_slug/:submission_id/DownloadPage](./docs/web/submission-base-files/section_slug.submission_id.DownloadPage.md) | GET | Files list (Option 2) |
| [/File/:file_id](./docs/web/submission-base-files/File.file_id.md) | GET | File contents |
| [/:section_slug/:submission_id/Issues](./docs/web/submission-base-issues/section_slug.submission_id.Issues.md) | GET | Issues list |
| [/:section_slug/:submission_id/Issue/Add](./docs/web/submission-base-issues/section_slug.submission_id.Issue.Add.md) | POST | [Auth] Add an Issue |
| [/Issue/:issue_id](./docs/web/submission-base-issues/Issue.issue_id.md) | PATCH | [Auth] Edit an Issue |
| [/Issue/:issue_id](./docs/web/submission-base-issues/Issue.issue_id.md) | DELETE | [Auth] Trash an Issue |
| [/:section_slug/:submission_id](./docs/web/submission-base-likes/section_slug.submission_id.md) | GET | Like count |
| [/:section_slug/:submission_id/Likes](./docs/web/submission-base-likes/section_slug.submission_id.Likes.md) | GET | Users who liked |
| [/:section_slug/:submission_id/Like](./docs/web/submission-base-likes/section_slug.submission_id.Like.md) | POST | [Auth] Like |
| [/:section_slug/:submission_id/Like](./docs/web/submission-base-likes/section_slug.submission_id.Like.md) | DELETE | [Auth] Unlike |
| [/Post/:post_id/ProfilePage](./docs/web/submission-base-posts---replies/Post.post_id.ProfilePage.md) | GET | Post / Reply properties |
| [/:section_slug/:submission_id](./docs/web/submission-base-posts---replies/section_slug.submission_id.md) | GET | Posts count |
| [/:section_slug/:submission_id/Posts](./docs/web/submission-base-posts---replies/section_slug.submission_id.Posts.md) | GET | Posts feed |
| [/:section_slug/:submission_id/Post/Add](./docs/web/submission-base-posts---replies/section_slug.submission_id.Post.Add.md) | POST | [Auth] Add a Post |
| [/Post/:post_id](./docs/web/submission-base-posts---replies/Post.post_id.md) | POST | [Auth] Add a Reply |
| [/Post/:post_id](./docs/web/submission-base-posts---replies/Post.post_id.md) | DELETE | [Auth] Trash a Post / Reply |
| [/Post/:post_id/Untrash](./docs/web/submission-base-posts---replies/Post.post_id.Untrash.md) | PATCH | [Auth] Untrash a Post / Reply |
| [/:section_slug/:submission_id](./docs/web/submission-base-properties/section_slug.submission_id.md) | GET | Multiple Properties (Option 1) |
| [/:section_slug/:submission_id/ProfilePage](./docs/web/submission-base-properties/section_slug.submission_id.ProfilePage.md) | GET | Multiple Properties (Option 2) |
| [/:section_slug/:submission_id](./docs/web/submission-base-subscription/section_slug.submission_id.md) | GET | Subscribers count |
| [/:section_slug/:submission_id/Subscribers](./docs/web/submission-base-subscription/section_slug.submission_id.Subscribers.md) | GET | Users who subscribed |
| [/:section_slug/:submission_id/Subscription/Add](./docs/web/submission-base-subscription/section_slug.submission_id.Subscription.Add.md) | POST | [Auth] Subscribe |
| [/Subscription/:subscription_id](./docs/web/submission-base-subscription/Subscription.subscription_id.md) | DELETE | [Auth] Unsubscribe |
| [/:section_slug/:submission_id](./docs/web/submission-base-thanks/section_slug.submission_id.md) | GET | Thanks count |
| [/:section_slug/:submission_id/Thanks](./docs/web/submission-base-thanks/section_slug.submission_id.Thanks.md) | GET | Users who thanked |
| [/:section_slug/:submission_id/Thank/Add](./docs/web/submission-base-thanks/section_slug.submission_id.Thank.Add.md) | POST | [Auth] Thank |
| [/:section_slug/:submission_id/Todos](./docs/web/submission-base-todos/section_slug.submission_id.Todos.md) | GET | Todos list |
| [/:section_slug/:submission_id/Todo/Add](./docs/web/submission-base-todos/section_slug.submission_id.Todo.Add.md) | POST | [Auth] Add a Todo |
| [/Todo/:todo_id](./docs/web/submission-base-todos/Todo.todo_id.md) | PATCH | [Auth] Edit a Todo |
| [/Todo/:todo_id/Toggle](./docs/web/submission-base-todos/Todo.todo_id.Toggle.md) | PATCH | [Auth] Toggle state |
| [/Todo/:todo_id](./docs/web/submission-base-todos/Todo.todo_id.md) | DELETE | [Auth] Trash a Todo |
| [/:section_slug/:submission_id](./docs/web/submission-base-updates/section_slug.submission_id.md) | GET | Updates count |
| [/:section_slug/:submission_id/Updates](./docs/web/submission-base-updates/section_slug.submission_id.Updates.md) | GET | Updates list |
| [/:section_slug/:submission_id/Files](./docs/web/submission-base-updates/section_slug.submission_id.Files.md) | GET | Files |
| [/:section_slug/:submission_id/Update](./docs/web/submission-base-updates/section_slug.submission_id.Update.md) | POST | [Auth] Add an Update |
| [/Update/:update_id](./docs/web/submission-base-updates/Update.update_id.md) | PATCH | [Auth] Edit an Update |
| [/Update/:update_id](./docs/web/submission-base-updates/Update.update_id.md) | DELETE | [Auth] Trash an Update |
| [/Update/:update_id/Untrash](./docs/web/submission-base-updates/Update.update_id.Untrash.md) | PATCH | [Auth] Untrash an Update |

### Submission - Specific Types

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/App/:submission_id/Users](./docs/web/submission-app/App.submission_id.Users.md) | GET | Users |
| [/App/:submission_id/CustomConfig/:app_config_id](./docs/web/submission-app/App.submission_id.CustomConfig.app_config_id.md) | GET | Custom config |
| [/Collection/:submission_id/Items](./docs/web/submission-collection/Collection.submission_id.Items.md) | GET | Items |
| [/Contest/:submission_id/Winners](./docs/web/submission-contest/Contest.submission_id.Winners.md) | GET | Winners |
| [/Idea/:submission_id/Ratings](./docs/web/submission-idea/Idea.submission_id.Ratings.md) | GET | Ratings list |
| [/Jam/:submission_id/Bounty/Contributors](./docs/web/submission-jam/Jam.submission_id.Bounty.Contributors.md) | GET | Bounty contributors |
| [/Jam/:submission_id/Bounty/Recipients](./docs/web/submission-jam/Jam.submission_id.Bounty.Recipients.md) | GET | Bounty recipients |
| [/Jam/:submission_id/Entries](./docs/web/submission-jam/Jam.submission_id.Entries.md) | GET | Entries list |
| [/Poll/:submission_id/Votes](./docs/web/submission-poll/Poll.submission_id.Votes.md) | GET | Votes |
| [/Project/:submission_id/FinishedWorks](./docs/web/submission-project/Project.submission_id.FinishedWorks.md) | GET | Finished works list |
| [/Project/:submission_id/Wips](./docs/web/submission-project/Project.submission_id.Wips.md) | GET | Wips list |
| [/Request/:submission_id/BountyRecipients](./docs/web/submission-request/Request.submission_id.BountyRecipients.md) | GET | Bounty recipients |
| [/Request/:submission_id/Bounty/Contributors](./docs/web/submission-request/Request.submission_id.Bounty.Contributors.md) | GET | Bounty contributors |

### Ripe

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/Ripe/Info](./docs/web/ripe/Ripe.Info.md) | GET | Info |
| [/Ripe/Purchasers](./docs/web/ripe/Ripe.Purchasers.md) | GET | Latest purchasers |

### Dictionaries

| Endpoint | Method | Description |
|----------|--------|-------------|
| [/Util/Config/TrashReasons](./docs/web/dictionaries/Util.Config.TrashReasons.md) | GET | Trash reasons |

---

## Official API

> **Base URL**: `https://api.gamebanana.com`

The Official API is documented separately. See the endpoint files in `docs/endpoints/`.

| Category | Endpoints |
|----------|-----------|
| Core / App | Authenticate |
| Core / Item | Data, IdentifyById |
| Core / List | Like, New, Section |
| Core / Member | Match, Identify, IdentifyById |
| RSS | Featured, New |

---

## Quick Reference

### Common Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `_nPage` | Page number | 1 |
| `_nPerpage` | Results per page (max 50) | 20 |
| `_sModelName` | Section type | - |
| `_sOrder` | Sort order | best_match |
| `_idGameRow` | Game ID filter | - |

### Sort Orders

- `best_match` - Relevance
- `popularity` - Most popular
- `date` - Newest
- `udate` - Recently updated

### Section Types (Model Names)

```
App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, 
Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, 
Question, Review, Request, Script, Sound, Spray, Studio, 
Thread, Tool, Tutorial, Wiki, Wip
```

### Response Field Prefixes

| Prefix | Type |
|--------|------|
| `_a` | Array |
| `_b` | Boolean |
| `_idRow` | ID |
| `_n` | Number |
| `_s` | String |
| `_ts` | Timestamp |

### Pagination

Check `_aMetadata._bIsComplete` - if `false`, there are more pages.

```json
{
  "_aMetadata": {
    "_nRecordCount": 285,
    "_bIsComplete": false
  }
}
```

---

*Generated from Postman Collection - gb-api-v11*
