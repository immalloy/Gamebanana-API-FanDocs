# GET /Game/Index

**By sort options and filters**

This endpoint returns a list of Games.

To sort results provide a value for _sSort

To filter results provide a value for _aFilters\[FILTER_NAME\]

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | Yes | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_nPerpage` | Yes | Integer. Records per page. Allowed values: >1 Default value: 5 |
| `_sSort` | Yes | oneOf. String. How to sort the records. Allowed values: see 'Sort options and filters' Default value: - |

