# Core / List / Section / AllowedFilterOperators

Returns a list of allowed operators for a given filter for [Core/List/Section](./Core.List.Section.md).

**Endpoint:** `GET api.gamebanana.com/Core/List/Section/AllowedFilterOperators?filter=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| filter | string | Filter (see [Core/List/Section/AllowedFilters](./Core.List.Section.AllowedFilters.md)). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/Section/AllowedFilterOperators?filter=udate&help)

## Error Examples

- [Error 1](/Core/List/Section/AllowedFilterOperators?filter=udte&help)
