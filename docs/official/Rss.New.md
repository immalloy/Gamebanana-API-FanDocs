# Rss / New

The newest SFW submissions formatted for RSS.

**Endpoint:** `GET api.gamebanana.com/Rss/New?`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string (Optional) | Type of submission or entity (see [Rss/New/AllowedItemTypes](./Rss.New.AllowedItemTypes.md)). Separate multiple itemtypes with commas. |
| gameid | int (Optional) | GameID of submission or entity. |
| userid | int (Optional) | UserID of submission or entity. |
| studioid | int (Optional) | StudioID of submission or entity. |
| include_updated | bool (Optional) | `1` or `true` - Return new & updated submissions.<br>`0` or `false` or if parameter omitted - Return new submissions only. |
| perpage | int (Optional) | Number of results to return (max 50). |

## Examples

- [Example 1](/Rss/New?&help)
- [Example 2](/Rss/New?gameid=5547&help)
- [Example 3](/Rss/New?userid=1382&help)
- [Example 4](/Rss/New?studioid=35086&help)

## Error Examples

- [Error 1](/Rss/New?userid=sdf&help)
- [Error 2](/Rss/New?itemtype=Skan&help)
- [Error 3](/Rss/New?studioid=0&help)
