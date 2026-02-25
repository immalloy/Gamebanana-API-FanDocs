# GET /Member/:id/SubFeed

**Latest (member)**

This endpoint returns a list of latest submissions of Member ID.

## Path Variables

| Variable | Description |
|----------|-------------|
| `id` | Required. Enter the Member's ID. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 20 |

