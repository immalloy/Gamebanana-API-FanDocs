# GET /Game/:id/Subfeed

**Latest (game)**

This endpoint returns a list of the latest submissions for the specified Game ID.

## Path Variables

| Variable | Description |
|----------|-------------|
| `id` | Required. Enter the Game's ID. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | Yes | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_sSort` | Yes | How to sort results.  Allowed values: default, new, updated  Default value: default |
| `_sName` | No | Enter the search query. Case insensitive.  Allowed values: string of 3 characters or more. |
| `_csvModelInclusions` | No | Comma-separated list of sections to include in the search results.  Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. |
| `_csvModelExclusions` | No | Comma-separated list of sections to exclude from the search results.  Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. |
| `_csvTagInclusions` | No | Comma-separated list of tags to include in the search results.  Allowed values: IDs as requested from Util/Generic/Tags endpoint. |
| `_csvTagExclusions` | No | Comma-separated list of tags to exclude from the search results.  Allowed values: IDs as requested from Util/Generic/Tags endpoint. |

