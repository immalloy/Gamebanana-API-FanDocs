# Core / Member / Match

Returns users matching the username.

**Endpoint:** `GET api.gamebanana.com/Core/Member/Match?username=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| username | string | User's username. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/Member/Match?username=tom&help)
- [Example 2](/Core/Member/Match?username=sdfsdfsdfsdfdsfsdfsdf&help)

## Error Examples

- [Error 1](/Core/Member/Match?username=&help)
