# GET /Util/Game/NameMatch

**By name**

This endpoint returns a list of Games containing the value of query parameter _sName in their names.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | Yes | Integer. Page to get. Allowed values: >1 Default value: 1 |
| `_nPerpage` | Yes | Integer. Records per page. Allowed values: >1 Default value: 5 |
| `_sName` | Yes | Required. String. Search query. Allowed values: >=3 characters Default value: - |

