# GET /Util/List/Featured

**Featured**

This endpoint returns a list of featured submissions.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 20 |
| `_sModelName` | No | oneOf. Narrow down the search to a specific section.  Allowed values: App, Article, Blog, Contest, Concept, Event, Idea, Mod, Model, News, Poll, Question, Review, Script, Sound, Spray, Thread, Tool, Tutorial, Wip. |
| `_idGameRow` | No | oneOf. Narrow down the search to a specific Game's ID. |

