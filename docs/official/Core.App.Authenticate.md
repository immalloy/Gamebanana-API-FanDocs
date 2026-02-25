# Core / App / Authenticate

Validates your app's API password, App ID and user ID and returns an authentication token on success.

**Endpoint:** `GET api.gamebanana.com/Core/App/Authenticate?api_password=...&app_id=...&userid=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| api_password | string | Your app's API password. |
| app_id | int | Your app's ID. |
| userid | int | The app user's ID. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/App/Authenticate?api_password=fred&app_id=2&userid=1382&help)

## Error Examples

- [Error 1](/Core/App/Authenticate?api_password=fred&app_id=2&userid=&help)
- [Error 2](/Core/App/Authenticate?api_password=fred&app_id=&userid=1382&help)
