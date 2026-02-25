# Core / Member / IdentifyById

Returns the user's username if found, or false if not found.

**Endpoint:** `GET api.gamebanana.com/Core/Member/IdentifyById?userid=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| userid | int | User's ID. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

*Multicall Enabled* - Make each parameter an array to perform multiple calls in a single request.

## Examples

- [Example 1](/Core/Member/IdentifyById?userid=1382&help)
- [Example 2](/Core/Member/IdentifyById?userid=9999999&help)

## Multicall Examples

- [Example 1](/Core/Member/IdentifyById?userid[]=9999999&userid[]=37&help)

## Error Examples

- [Error 1](/Core/Member/IdentifyById?userid[]=&userid[]=37&help)
- [Error 2](/Core/Member/IdentifyById?userid=ddfgdfg&help)
