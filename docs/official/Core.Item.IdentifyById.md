# Core / Item / IdentifyById

Returns true if the item is found, or false if not found.

**Endpoint:** `GET api.gamebanana.com/Core/Item/IdentifyById?itemtype=...&itemid=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/Item/Data/AllowedItemTypes](./Core.Item.Data.AllowedItemTypes.md)). |
| itemid | int | ID of the itemtype. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

*Multicall Enabled* - Make each parameter an array to perform multiple calls in a single request.

## Examples

- [Example 1](/Core/Item/IdentifyById?itemtype=Member&itemid=1382&help)

## Multicall Examples

- [Example 1](/Core/Item/IdentifyById?itemtype[]=Blog&itemtype[]=Member&itemid[]=999999&itemid[]=1382&help)

## Error Examples

- [Error 1](/Core/Item/IdentifyById?itemtype=Cat&itemid=1382&help)
- [Error 2](/Core/Item/IdentifyById?itemtype[]=Bog&itemtype[]=Member&itemid[]=999999&itemid[]=37&help)
