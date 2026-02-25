# GET /Util/Search/Results

**Advanced search**

This endpoint returns a list of search results.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_sSearchString` | Yes | Required. Enter the search query. Case insensitive.  Allowed values: string of 2 characters or more. |
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 20 |
| `_sModelName` | No | Narrow down the search to a specific section.  Allowed values: App, Article, Bug, Blog, Club, Contest, Concept, Event, Game, Idea, Initiative, Jam, Mod, Model, Member, News, Poll, Project, Question, Review, Request, Script, Sound, Spray, Studio, Thread, Tool, Tutorial, Wiki, Wip. |
| `_sOrder` | No | How to sort results.  Allowed values: best_match, popularity, date, udate  Default value: best_match  best_match == Relevance popularity == Popularity date == Newest udate == Updated |
| `_csvFields` | No | Comma-separated list of search fields.  Allowed values: name, description, article, attribs, studio, owner, credits  Default value: name,description,article,attribs,studio,owner,credits  name == Name description == Description article == Blurb/Readme attribs == Tags studio == Studio owner == Submitter credits == Credits |
| `_idGameRow` | No | Narrow down the search to a specific Game's ID. |

