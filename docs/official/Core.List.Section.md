# Core / List / Section

Returns submission or entity IDs by section.

**Endpoint:** `GET api.gamebanana.com/Core/List/Section?itemtype=...&sort=...&direction=...&page=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/List/Section/AllowedItemTypes](./Core.List.Section.AllowedItemTypes.md)). |
| sort | string | Field to sort by (see [Core/List/Section/AllowedSorts](./Core.List.Section.AllowedSorts.md)). |
| direction | string | `asc` - Sort ascending.<br>`desc` or if parameter omitted - Sort descending. |
| page | int | Result page. |
| filter | string (Optional) | Field to filter by (see [Core/List/Section/AllowedFilters](./Core.List.Section.AllowedFilters.md)). |
| filterval | mixed (Optional) | Filter value |
| filterop | string (Optional) | Filter operator (see [Core/List/Section/AllowedFilterOperators](./Core.List.Section.AllowedFilterOperators.md)). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/Section?itemtype=Map&sort=name&direction=desc&page=1&help)
- [Example 2](/Core/List/Section?itemtype=Map&sort=name&direction=asc&page=1&help)
- [Example 3](/Core/List/Section?itemtype=Map&sort=id&direction=desc&page=1&filter=udate&filterval=1382&filterop=greater_than&help)

## Error Examples

- [Error 1](/Core/List/Section?itemtype=Meber&sort=id&direction=asc&help)
- [Error 2](/Core/List/Section?itemtype=Map&sort=sdf&direction=desc&help)
