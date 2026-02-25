# Core / List / Section / AllowedSorts

Returns a list of allowed sorts for a given itemtype for Core/List/Section.

**Endpoint:** `GET api.gamebanana.com/Core/List/Section/AllowedSorts?itemtype=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/List/Section/AllowedItemTypes](./Core.List.Section.AllowedItemTypes.md)). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/Section/AllowedSorts?itemtype=Member&help)
- [Example 2](/Core/List/Section/AllowedSorts?itemtype=Game&help)

## Error Examples

- [Error 1](/Core/List/Section/AllowedSorts?itemtype=Tol&help)
