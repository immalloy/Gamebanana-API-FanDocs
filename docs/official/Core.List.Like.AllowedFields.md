# Core / List / Like / AllowedFields

Returns a list of allowed fields for a given itemtype for [Core/List/Like](./Core.List.Like.md).

**Endpoint:** `GET api.gamebanana.com/Core/List/Like/AllowedFields?itemtype=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/List/Like/AllowedItemTypes](./Core.List.Like.AllowedItemTypes.md)). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/Like/AllowedFields?itemtype=Member&help)
- [Example 2](/Core/List/Like/AllowedFields?itemtype=Game&help)

## Error Examples

- [Error 1](/Core/List/Like/AllowedFields?itemtype=Tol&help)
