# Core / List / Like

Returns submissions or entities matching the start of a field.

**Endpoint:** `GET api.gamebanana.com/Core/List/Like?itemtype=...&field=...&match=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/List/Like/AllowedItemTypes](./Core.List.Like.AllowedItemTypes.md)). |
| field | string | Field to match (see [Core/List/Like/AllowedFields](./Core.List.Like.AllowedFields.md)). |
| match | string | Start of the field value (minimum 2 chars). |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

## Examples

- [Example 1](/Core/List/Like?itemtype=Member&field=name&match=natk&help)
- [Example 2](/Core/List/Like?itemtype=Member&field=name&match=natko&help)
- [Example 3](/Core/List/Like?itemtype=Member&field=name&match=natko123123&help)

## Error Examples

- [Error 1](/Core/List/Like?itemtype=Meber&field=name&match=natk&help)
- [Error 2](/Core/List/Like?itemtype=Member&field=nme&match=natko&help)
- [Error 3](/Core/List/Like?itemtype=Member&field=name&match=n&help)
