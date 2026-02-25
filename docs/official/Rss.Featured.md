# Rss / Featured

The last 10 featured submissions formatted for RSS.

**Endpoint:** `GET api.gamebanana.com/Rss/Featured?`

## Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| itemtype | string (Optional) | Type of submission or entity (see [Rss/Featured/AllowedItemTypes](./Rss.Featured.AllowedItemTypes.md)). |
| gameid | int (Optional) | GameID of submission or entity. |
| userid | int (Optional) | UserID of submission or entity. |
| studioid | int (Optional) | StudioID of submission or entity. |

## Examples

- [Example 1](/Rss/Featured?&help)
- [Example 2](/Rss/Featured?gameid=5547&help)
- [Example 3](/Rss/Featured?userid=1382&help)
- [Example 4](/Rss/Featured?studioid=35086&help)

## Error Examples

- [Error 1](/Rss/Featured?userid=sdf&help)
- [Error 2](/Rss/Featured?itemtype=Skan&help)
- [Error 3](/Rss/Featured?studioid=0&help)
