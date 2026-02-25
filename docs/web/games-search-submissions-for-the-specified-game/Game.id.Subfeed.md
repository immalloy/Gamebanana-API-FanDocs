# GET /Game/:id/Subfeed

**Advanced search**

This endpoint returns a list of submissions for the specified Game ID.

## Path Variables

| Variable | Description |
|----------|-------------|
| `id` | Required. Integer. Game ID. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | Yes | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_sSort` | Yes | String. How to sort the records. Allowed values: new, default, updated Default value: - |
| `_sName` | Yes | String. Search query. Allowed values: >=3 characters Default value: - |
| `_csvModelInclusions` | No | String. Comma-separated list of sections to include in the search results. Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. Default value: - |
| `_csvModelExclusions` | No | String. Comma-separated list of sections to exclude from the search results. Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. Default value: - |
| `_csvTagInclusions` | No | String. Comma-separated list of tags to include in the search results. Allowed values: tag IDs. See 'Search/Tags by text'. Default value: - |
| `_csvTagExclusions` | No | String. Comma-separated list of tags to exclude from the search results. Allowed values: tag IDs. See 'Search/Tags by text'. Default value: - |

