# Core / Member / Identify

Returns the user's ID if found, or false if not found.

**Endpoint:** `GET api.gamebanana.com/Core/Member/Identify?username=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| username | string | User's username. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

*Multicall Enabled* - Make each parameter an array to perform multiple calls in a single request.

## Examples

- [Example 1](/Core/Member/Identify?username=tom&help)
- [Example 2](/Core/Member/Identify?username=sdfsdfsdfsdfdsfsdfsdf&help)

## Multicall Examples

- [Example 1](/Core/Member/Identify?username[]=sdfsdfsdfsdfdsfsdfsdf&username[]=tom&help)

## Error Examples

- [Error 1](/Core/Member/Identify?username=&help)
- [Error 2](/Core/Member/Identify?username[]=&username[]=mini&help)
