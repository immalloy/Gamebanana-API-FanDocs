# Core / Item / Data

Returns data on the submission or entity.

**Endpoint:** `GET api.gamebanana.com/Core/Item/Data?itemtype=...&itemid=...&fields=...`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string | Type of submission or entity (see [Core/Item/Data/AllowedItemTypes](./Core.Item.Data.AllowedItemTypes.md)). |
| itemid | int | ID of the itemtype. |
| fields | string | Comma delimited fields (see [Core/Item/Data/AllowedFields](./Core.Item.Data.AllowedFields.md)). |
| return_keys | bool (Optional) | `1` or `true` - Return values with field names.<br>`0` or `false` or if parameter omitted - Return values only. |
| return_object | bool (Optional) | **Deprecated** - Use return_keys.<br>`1` or `true` - Return values with field names.<br>`0` or `false` or if parameter omitted - Return values only. |
| format | string (Optional) | `json` - Return prettified JSON (default)<br>`json_min` - Return minified JSON<br>`xml` - Return XML<br>`php_serialized` - Return PHP serialize()'d data |
| flags | string (Optional) | Comma delimited flags.<br>`JSON_UNESCAPED_SLASHES` - Don't escape / (applies to JSON responses only) |

*Multicall Enabled* - Make each parameter an array to perform multiple calls in a single request.

## Examples

- [Example 1](/Core/Item/Data?itemtype=Member&itemid=1382&fields=name,Buddies().Count().nCount(),Modgroup().bIsInAnyModgroup(),Modgroup().aModgroupsMemberIsPartOf()&help)
- [Example 2](/Core/Item/Data?itemtype=Map&itemid=191108&fields=name,Posts().LastPost().idPosterRow(),Posts().LastPost().sText()&help)

## Multicall Examples

- [Example 1](/Core/Item/Data?itemtype[]=Blog&itemtype[]=Member&itemid[]=18235&itemid[]=1382&fields[]=userid&fields[]=name&help)
- [Example 2](/Core/Item/Data?itemtype[]=Blog&itemtype[]=Member&itemid[]=18235&itemid[]=1382&fields[]=userid,name&fields[]=name,user_title&help)

## Error Examples

- [Error 1](/Core/Item/Data?itemtype=Memer&itemid=1382&fields=name,Buddies().Count().nCount(),Modgroup().bIsInAnyModgroup(),Modgroup().aModgroupsMemberIsPartOf()&help)
- [Error 2](/Core/Item/Data?itemtype=Map&itemid=191108&fields=namePosts().LastPost().idPosterRow(),Posts().LastPost().sText()&help)
- [Error 3](/Core/Item/Data?itemtype[]=log&itemtype[]=Member&itemid[]=18235&itemid[]=1382&fields[]=userid&fields[]=name&help)
