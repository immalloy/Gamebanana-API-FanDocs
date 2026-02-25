# GET /Util/Generic/Discussions

**Multiple Discussions**

Returns a list of the latests discussions.

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | No | Integer. Page to get.  Allowed values: >1  Default value: 1 |
| `_idStudioRow` | No | [oneOf] Integer. Discussions in the specific Studio. |
| `_idMemberRow` | No | [oneOf] Integer. Discussions by the specific Member. |
| `_idGameRow` | No | [oneOf] Integer. Discussions about the specific Game. |

