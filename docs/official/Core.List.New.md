# Core / List / New

New submissions.

**Endpoint:** `GET api.gamebanana.com/Core/List/New?page=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| page | int | Result page. |
| itemtype | string (Optional) | Type of submission or entity (see [Core/List/New/AllowedItemTypes](./Core.List.New.AllowedItemTypes.md)). Separate multiple itemtypes with commas. |
| gameid | int (Optional) | GameID of submission or entity. Separate multiple IDs with commas. |
| userid | int (Optional) | UserID of submission or entity. |
| studioid | int (Optional) | StudioID of submission or entity. |
| max_age | int (Optional) | Maximum age of submissions, in seconds. |
| include_updated | bool (Optional) | `1` or `true` - Return new & updated submissions.<br>`0` or `false` or if parameter omitted - Return new submissions only. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/New?page=1&help)
- [Example 2](/Core/List/New?gameid=5547&page=1&help)
- [Example 3](/Core/List/New?userid=1382&page=1&help)
- [Example 4](/Core/List/New?studioid=35086&page=1&help)

## Error Examples

- [Error 1](/Core/List/New?userid=1382&help)
- [Error 2](/Core/List/New?userid=sdf&page=1&help)
- [Error 3](/Core/List/New?itemtype=Skan&page=1&help)
- [Error 4](/Core/List/New?studioid=0&page=1&help)
