# GET /Util/Game/NameMatch

**Games by name**

This endpoint returns a list of games containing the search query in their names.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_sName` | Yes | Required. Enter the search query. Case insensitive.  Allowed values: string of 3 characters or more. |
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 10 |

