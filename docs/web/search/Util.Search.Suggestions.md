# GET /Util/Search/Suggestions

**Search suggestions**

This endpoint returns a list of suggested search queries for the provided search string.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_sSearchString` | Yes | Required. Enter the search query. Case insensitive.  Allowed values: string of 2 characters or more. |
| `_sModelName` | Yes | Required. Narrow down the search to a specific section.  Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. |
| `_idGameRow` | No | Narrow down the search to a specific Game's ID. |

