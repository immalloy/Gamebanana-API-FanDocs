# Core / Item / Data / AllowedFields

Returns a list of allowed fields for a given itemtype for [Core/Item/Data](./Core.Item.Data.md).

**Endpoint:** `GET api.gamebanana.com/Core/Item/Data/AllowedFields?itemtype=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/Item/Data/AllowedItemTypes](./Core.Item.Data.AllowedItemTypes.md)). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/Item/Data/AllowedFields?itemtype=Member&help)
- [Example 2](/Core/Item/Data/AllowedFields?itemtype=Tool&help)

## Error Examples

- [Error 1](/Core/Item/Data/AllowedFields?itemtype=Tol&help)
