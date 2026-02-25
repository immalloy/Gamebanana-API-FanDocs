# GET /Util/Homepage/Submissions

**Latest (all games)**

This endpoint returns a list of the latest submissions displayed on the homepage (all games are included).

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 20 |
| `_sSort` | No | How to sort results.  Allowed values: default, new, updated  Default value: default |
| `_bFilterBySubscribedGames` | No | If provided, show submissions for the games the effective user is subscribed to.  Has no effect on guests.  Allowed values: true, false  Default value: false |

