# GameBanana API v11 (Web API) - Complete Reference

> **Source**: Semi-official Postman Collection Documentation
> **Base URL**: `https://gamebanana.com/apiv11`
> **Total Endpoints**: 104

---

## Table of Contents

1. [Search & Discovery](#search--discovery)
2. [Games](#games)
3. [Work in Progress](#work-in-progress)
4. [Authentication](#authentication)
5. [Submission - Base](#submission---base)
6. [Submission - Specific Types](#submission---specific-types)
7. [Ripe](#ripe)
8. [Dictionaries](#dictionaries)

---

## Search & Discovery

### /:model_name

#### `GET` /:model_name/ListFilterConfig

**Search modificators**

This endpoint returns filters configuration for API Index.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `model_name` | path | Required. Enter the model name. |

---

#### `GET` /:model_name/Index

**Latest (section)**

This endpoint returns a list of records matching the given criteria.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `model_name` | path | Required. Enter the model name. |

---

### /Game

#### `GET` /Game/:id/Subfeed

**Latest (game)**

This endpoint returns a list of the latest submissions for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Enter the Game's ID. |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_sSort` | How to sort results.  Allowed values: default, new, updated  Default value: default |

---

#### `GET` /Game/:id/TopSubs

**Top (game)**

This endpoint returns top submissions displayed on the game's homepage.

Available periods:

- day
- week
- month
- 3 months
- 6 months
- year
- all time

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Enter the Game's ID. |

---

#### `GET` /Game/ListFilterConfig

**Sort options and filters**

This endpoint returns a set of available sort options and filters.

---

#### `GET` /Game/Index

**By sort options and filters**

This endpoint returns a list of Games.

To sort results provide a value for _sSort

To filter results provide a value for _aFilters\[FILTER_NAME\]

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_nPerpage` | Integer. Records per page. Allowed values: >1 Default value: 5 |
| `_sSort` | oneOf. String. How to sort the records. Allowed values: see 'Sort options and filters' Default value: - |

---

#### `GET` /Game/:id/TopSubs

**Top submissions**

This endpoint returns top submissions displayed on the homepage of the specified Game ID.

There might be top submissions for the following periods:

- day
- week
- month
- 3 months
- 6 months
- year
- all time

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

---

#### `GET` /Game/:id/CommunitySpotlight

**Community Spotlight**

This endpoint returns a set of submissions, studios and clubs that have gained popularity recently for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

---

#### `GET` /Game/:id/Subfeed

**Advanced search**

This endpoint returns a list of submissions for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_sSort` | String. How to sort the records. Allowed values: new, default, updated Default value: - |
| `_sName` | String. Search query. Allowed values: >=3 characters Default value: - |

---

### /Member

#### `GET` /Member/:id/SubFeed

**Latest (member)**

This endpoint returns a list of latest submissions of Member ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Enter the Member's ID. |

---

### /Util

#### `GET` /Util/Search/Results

**Advanced search**

This endpoint returns a list of search results.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_sSearchString` | Required. Enter the search query. Case insensitive.  Allowed values: string of 2 characters or more. |

---

#### `GET` /Util/Search/Suggestions

**Search suggestions**

This endpoint returns a list of suggested search queries for the provided search string.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_sSearchString` | Required. Enter the search query. Case insensitive.  Allowed values: string of 2 characters or more. |
| `_sModelName` | Required. Narrow down the search to a specific section.  Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. |

---

#### `GET` /Util/Game/NameMatch

**Games by name**

This endpoint returns a list of games containing the search query in their names.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_sName` | Required. Enter the search query. Case insensitive.  Allowed values: string of 3 characters or more. |

---

#### `GET` /Util/Generic/Tags

**Tags by text**

This endpoint returns a list of tags containing the search query in their names.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_sTag` | Required. Enter the search query. Case insensitive.  Allowed values: string of 2 characters or more. |

---

#### `GET` /Util/Homepage/Submissions

**Latest (all games)**

This endpoint returns a list of the latest submissions displayed on the homepage (all games are included).

---

#### `GET` /Util/List/Featured

**Featured**

This endpoint returns a list of featured submissions.

---

#### `GET` /Util/Homepage/TopGames

**Trending, Classics, New**

This endpoint returns lists of Trending, Classics, New games.

---

#### `GET` /Util/Game/NameMatch

**By name**

This endpoint returns a list of Games containing the value of query parameter _sName in their names.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_nPerpage` | Integer. Records per page. Allowed values: >1 Default value: 5 |
| `_sName` | Required. String. Search query. Allowed values: >=3 characters Default value: - |

---

#### `GET` /Util/List/Featured

**Featured**

This endpoint returns a list of submissions that were previously featured on the homepage of the specified Game ID.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_idGameRow` | Required. Integer. Game ID. |

---

## Games

### /Game

#### `GET` /Game/:id/ProfilePage

**Multiple Properties (1)**

This endpoint returns multiple properties for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

---

#### `GET` /Game/:id

**Multiple Properties (2)**

This endpoint returns multiple properties for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` | String. Comma-separated list of properties to request. Allowed values: see response body. Default value: - |

---

#### `GET` /Game/:id/GetStartedPage

**Detailed information**

This endpoint returns detailed information for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

---

#### `GET` /Game/:id/Rules

**Additional rules**

This endpoint returns a list of additional rules for the specified Game ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Integer. Game ID. |

---

### /Util

#### `GET` /Util/Generic/Discussions

**Discussions**

This endpoint returns a list of the latest discussions for the specified Game ID.

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_idGameRow` | Required. Integer. Game ID. |

---

## Work in Progress

### /:sectionSlug

#### `GET` /:sectionSlug/Categories

**Multiple RootCategories**

Returns a list of the root categories by Section Slug.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `sectionSlug` | path | Required. Section slug. |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_sSort` | Required. String. How to sort the results.   Allowed values: a_to_z, count  Default value: - |

---

### /Member

#### `GET` /Member/:id/AwardedBounties

**Awarded Bounties**

Returns a list of submissions the specified Member ID has been awarded bounties for.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/ContributedBounties

**Contributed Bounties**

Returns a list of submissions the specified Member ID has contributed bounties for.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/LikedSubmissions

**Liked Submissions**

Returns a list of submissions liked by a specified Member ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/Medals

**Medals**

Returns a list of medals for a specified Member ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/ParticipatedContests

**Participated Contests**

Returns a list of contests the specified Member ID has participated in.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/RatedIdeas

**Rated Ideas**

Returns a list of ideas the specified Member ID has rated.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/SolvedQuestions

**Solved Questions**

Returns a list of questions solved by the specified Member ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/ThankedSubmissions

**Thanked Submissions**

Returns a list of submissions the specified Member ID has thanked.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/VotedPolls

**Voted Polls**

Returns a list of polls the specified Member ID has voted in.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/Submissions/Contributions

**Contributions**

Returns a list of submissions where the specified Member ID has been listed in the credits.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

#### `GET` /Member/:id/Submissions/Posts

**Latest Posts**

Returns a list of posts made by a specified Member ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `id` | path | Required. Member ID. |

---

### /ModCategory

#### `GET` /ModCategory/:rootCategoryId/SubCategories

**Multiple SubCategories**

Returns a list of the sub categories by Root Category ID.

**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `rootCategoryId` | path | Required. Root category ID. |

---

### /Util

#### `GET` /Util/Generic/Discussions

**Multiple Discussions**

Returns a list of the latests discussions.

---

#### `GET` /Util/Homepage/Features

**Features**

Returns a list of featured submissions.

---

#### `GET` /Util/Homepage/CommunitySpotlight

**CommunitySpotlight**

Returns a set of submissions, studios and clubs that have gained popularity recently.

---

## Authentication

### /Member

#### `POST` /Member/Authenticate

**Authenticate**



---

#### `POST` /Member/EmailAuthenticate

**1. Request confirmation code**



---

#### `POST` /Member/EmailAuthenticate

**2. Submit confirmation code**



---

## Submission - Base

### /:section_slug

#### `GET` /:section_slug/:submission_id

**Multiple Properties (Option 1)**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/ProfilePage

**Multiple Properties (Option 2)**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Files list (Option 1)**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/DownloadPage

**Files list (Option 2)**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id/Collections

**Collections added to**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /:section_slug/:submission_id/AccessorCollections

**Accessor collections**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `POST` /:section_slug/:submission_id/AddToCollection

**[Auth] Add to Collection**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `DELETE` /:section_slug/:submission_id/RemoveFromCollection

**[Auth] Remove from Collection**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id/EmbeddablesPage

**Embeds list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id/Issues

**Issues list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `POST` /:section_slug/:submission_id/Issue/Add

**[Auth] Add an Issue**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Like count**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/Likes

**Users who liked**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `POST` /:section_slug/:submission_id/Like

**[Auth] Like**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `DELETE` /:section_slug/:submission_id/Like

**[Auth] Unlike**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Posts count**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/Posts

**Posts feed**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |
| `_nPerpage` |  |
| `_sSort` |  |

---

#### `POST` /:section_slug/:submission_id/Post/Add

**[Auth] Add a Post**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Subscribers count**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/Subscribers

**Users who subscribed**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `POST` /:section_slug/:submission_id/Subscription/Add

**[Auth] Subscribe**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Thanks count**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/Thanks

**Users who thanked**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `POST` /:section_slug/:submission_id/Thank/Add

**[Auth] Thank**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id/Todos

**Todos list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `POST` /:section_slug/:submission_id/Todo/Add

**[Auth] Add a Todo**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `GET` /:section_slug/:submission_id

**Updates count**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_csvProperties` |  |

---

#### `GET` /:section_slug/:submission_id/Updates

**Updates list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |
| `_nPerpage` |  |

---

#### `GET` /:section_slug/:submission_id/Files

**Files**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

#### `POST` /:section_slug/:submission_id/Update

**[Auth] Add an Update**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `section_slug` | path |  |
| `submission_id` | path |  |

---

### /Collection

#### `POST` /Collection/Add

**[Auth] Create a Collection**



---

### /File

#### `GET` /File/:file_id

**File contents**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `file_id` | path |  |

---

### /Issue

#### `PATCH` /Issue/:issue_id

**[Auth] Edit an Issue**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `issue_id` | path |  |

---

#### `DELETE` /Issue/:issue_id

**[Auth] Trash an Issue**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `issue_id` | path |  |

---

### /Post

#### `GET` /Post/:post_id/ProfilePage

**Post / Reply properties**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `post_id` | path |  |

---

#### `POST` /Post/:post_id

**[Auth] Add a Reply**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `post_id` | path |  |

---

#### `DELETE` /Post/:post_id

**[Auth] Trash a Post / Reply**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `post_id` | path |  |

---

#### `PATCH` /Post/:post_id/Untrash

**[Auth] Untrash a Post / Reply**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `post_id` | path |  |

---

### /Subscription

#### `DELETE` /Subscription/:subscription_id

**[Auth] Unsubscribe**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `subscription_id` | path |  |

---

### /Todo

#### `PATCH` /Todo/:todo_id

**[Auth] Edit a Todo**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `todo_id` | path |  |

---

#### `PATCH` /Todo/:todo_id/Toggle

**[Auth] Toggle state**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `todo_id` | path |  |

---

#### `DELETE` /Todo/:todo_id

**[Auth] Trash a Todo**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `todo_id` | path |  |

---

### /Update

#### `PATCH` /Update/:update_id

**[Auth] Edit an Update**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `update_id` | path |  |

---

#### `DELETE` /Update/:update_id

**[Auth] Trash an Update**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `update_id` | path |  |

---

#### `PATCH` /Update/:update_id/Untrash

**[Auth] Untrash an Update**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `update_id` | path |  |

---

## Submission - Specific Types

### /App

#### `GET` /App/:submission_id/Users

**Users**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /App/:submission_id/CustomConfig/:app_config_id

**Custom config**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |
| `app_config_id` | path |  |

---

### /Collection

#### `GET` /Collection/:submission_id/Items

**Items**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |
| `_nPerpage` |  |

---

### /Contest

#### `GET` /Contest/:submission_id/Winners

**Winners**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

---

### /Idea

#### `GET` /Idea/:submission_id/Ratings

**Ratings list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |
| `_nPerpage` |  |

---

### /Jam

#### `GET` /Jam/:submission_id/Bounty/Contributors

**Bounty contributors**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /Jam/:submission_id/Bounty/Recipients

**Bounty recipients**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /Jam/:submission_id/Entries

**Entries list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

### /Poll

#### `GET` /Poll/:submission_id/Votes

**Votes**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |
| `_nPerpage` |  |

---

### /Project

#### `GET` /Project/:submission_id/FinishedWorks

**Finished works list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /Project/:submission_id/Wips

**Wips list**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

### /Request

#### `GET` /Request/:submission_id/BountyRecipients

**Bounty recipients**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

#### `GET` /Request/:submission_id/Bounty/Contributors

**Bounty contributors**



**Path Variables**

| Variable | Type | Description |
|----------|------|-------------|
| `submission_id` | path |  |

**Query Parameters**

| Parameter | Description |
|-----------|-------------|
| `_nPage` |  |

---

## Ripe

### /Ripe

#### `GET` /Ripe/Info

**Info**

This endpoints returns Ripe info.

---

#### `GET` /Ripe/Purchasers

**Latest purchasers**



---

## Dictionaries

### /Util

#### `GET` /Util/Config/TrashReasons

**Trash reasons**



---

---

## Pagination

To paginate through APIs that return collections, check `_aMetadata._bIsComplete`. 
If `true`, there is another page to request.

```json
{
  "_aMetadata": {
    "_nRecordCount": 285,
    "_bIsComplete": false
  }
}
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `_nPage` | Page number (default: 1) |
| `_nPerpage` | Results per page (default: 20, max: 50) |
| `_sModelName` | Section name (Mod, Game, Tool, etc.) |
| `_sOrder` | Sort order (best_match, popularity, date, udate) |
| `_idGameRow` | Game ID to filter by |

---

## Section Names (Model Names)

The following section types can be used with `_sModelName`:

`App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip`

---

## Response Field Prefixes

GameBanana uses consistent prefixes for response fields:

| Prefix | Meaning |
|--------|---------|
| `_a` | Array |
| `_b` | Boolean |
| `_h` | Height (pixels) |
| `_idRow` | Database ID |
| `_n` | Number |
| `_s` | String |
| `_ts` | Timestamp |
| `_w` | Width (pixels) |

---

## Authentication

Some endpoints require authentication. These are marked with `[Auth]` in the name.

### Via Username
```
POST /Member/Authenticate
```

### Via Email
```
POST /Member/EmailAuthenticate
```

---

*Generated from Postman Collection - gb-api-v11*
