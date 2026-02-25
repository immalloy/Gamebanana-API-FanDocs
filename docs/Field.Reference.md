# GameBanana API - Response Field Reference

> Complete reference for all response field prefixes and common fields

---

## Field Prefix Conventions

GameBanana uses consistent prefixes for all API responses:

| Prefix | Type | Example |
|--------|------|---------|
| `_a` | Array | `_aRecords`, `_aTags` |
| `_b` | Boolean | `_bIsComplete`, `_bHasFiles` |
| `_h` | Height (px) | `_hFile220`, `_hImage` |
| `_idRow` | Integer ID | `_idRow`, `_idGameRow` |
| `_n` | Number | `_nRecordCount`, `_nPage` |
| `_s` | String | `_sName`, `_sProfileUrl` |
| `_ts` | Timestamp | `_tsDateAdded`, `_tsDateModified` |
| `_w` | Width (px) | `_wFile220`, `_wImage` |

---

## Metadata Fields

These fields appear in almost every response:

| Field | Type | Description |
|-------|------|-------------|
| `_aMetadata` | object | Response metadata |
| `_aMetadata._nRecordCount` | number | Total records available |
| `_aMetadata._nPerpage` | number | Records per page |
| `_aMetadata._bIsComplete` | boolean | `true` if last page |
| `_aRecords` | array | Array of result records |

---

## Common Record Fields

### Identification

| Field | Type | Description |
|-------|------|-------------|
| `_idRow` | number | Unique database ID |
| `_sModelName` | string | Type (Mod, Game, Tool, etc.) |
| `_sSingularTitle` | string | Display type (Mod, Game, Tool) |

### Content

| Field | Type | Description |
|-------|------|-------------|
| `_sName` | string | Name/title of the item |
| `_sDescription` | string | Description text |
| `_sArticle` | string | Full article/readme content |
| `_aTags` | array | Array of tag strings |

### URLs

| Field | Type | Description |
|-------|------|-------------|
| `_sProfileUrl` | string | Full URL to item page |
| `_sUrl` | string | Alternative URL |

### Media

| Field | Type | Description |
|-------|------|-------------|
| `_aPreviewMedia` | object | Preview images/videos |
| `_aPreviewMedia._aImages` | array | Array of image objects |
| `_aPreviewMedia._aVideos` | array | Array of video objects |

### Image Object Fields

| Field | Type | Description |
|-------|------|-------------|
| `_sType` | string | Type (screenshot, video, sticker) |
| `_sBaseUrl` | string | Base URL for image |
| `_sFile` | string | Filename |
| `_sFile220` | string | Thumbnail 220px wide |
| `_sFile530` | string | Thumbnail 530px wide |
| `_sFile800` | string | Large image 800px wide |
| `_hFile220` | number | Image height |
| `_wFile220` | number | Image width |

### Dates

| Field | Type | Description |
|-------|------|-------------|
| `_tsDateAdded` | timestamp | Creation date |
| `_tsDateModified` | timestamp | Last modified date |
| `_tsLastActivity` | timestamp | Last activity |

### Statistics

| Field | Type | Description |
|-------|------|-------------|
| `_nViewCount` | number | Total views |
| `_nDownloadCount` | number | Total downloads |
| `_nLikeCount` | number | Total likes |
| `_nCommentCount` | number | Total comments |
| `_nFollowerCount` | number | Total followers |
| `_nSubscriberCount` | number | Total subscribers |

### Status

| Field | Type | Description |
|-------|------|-------------|
| `_bHasFiles` | boolean | Has downloadable files |
| `_bHasPreview` | boolean | Has preview media |
| `_bIsFeatured` | boolean | Is featured |
| `_bIsLocked` | boolean | Is locked |
| `_bIsObsolete` | boolean | Is obsolete/deprecated |
| `_bIsPrivate` | boolean | Is private |

---

## Submitter/Owner Fields

| Field | Type | Description |
|-------|------|-------------|
| `_aSubmitter` | object | Submitter info |
| `_aSubmitter._idRow` | number | User ID |
| `_aSubmitter._sName` | string | Username |
| `_aSubmitter._bIsOnline` | boolean | Is online now |
| `_aSubmitter._sProfileUrl` | string | Profile URL |
| `_aSubmitter._sAvatarUrl` | string | Avatar image URL |

---

## Game Fields

| Field | Type | Description |
|-------|------|-------------|
| `_aGame` | object | Associated game |
| `_aGame._idRow` | number | Game ID |
| `_aGame._sName` | string | Game name |
| `_aGame._sProfileUrl` | string | Game page URL |
| `_aGame._sIconUrl` | string | Game icon |
| `_aGame._sBannerUrl` | string | Game banner |

---

## Category Fields

| Field | Type | Description |
|-------|------|-------------|
| `_aRootCategory` | object | Root category |
| `_aRootCategory._idRow` | number | Category ID |
| `_aRootCategory._sName` | string | Category name |
| `_aRootCategory._sProfileUrl` | string | Category URL |
| `_aSubCategory` | object | Sub-category (if any) |

---

## File Fields

| Field | Type | Description |
|-------|------|-------------|
| `_aFiles` | array | Array of files |
| `_aFiles[]._idRow` | number | File ID |
| `_aFiles[]._sFileName` | string | File name |
| `_aFiles[]._sDownloadUrl` | string | Download URL |
| `_aFiles[]._nFileSize` | number | File size in bytes |
| `_aFiles[]._nDownloadCount` | number | Download count |
| `_aFiles[]._sMd5Hash` | string | MD5 hash |

### Archive Tree (Web API Only)

| Field | Type | Description |
|-------|------|-------------|
| `_aArchiveFileTree` | object | Full ZIP contents |
| `_aArchiveFileTree._aFiles` | array | Files in archive |
| `_aArchiveFileTree._aFolders` | array | Folders in archive |

---

## Response Example

```json
{
  "_aMetadata": {
    "_nRecordCount": 100,
    "_nPerpage": 20,
    "_bIsComplete": false
  },
  "_aRecords": [
    {
      "_idRow": 650004,
      "_sModelName": "Mod",
      "_sSingularTitle": "Mod",
      "_sName": "My Awesome Mod",
      "_sProfileUrl": "https://gamebanana.com/mods/650004",
      "_tsDateAdded": 1699123456,
      "_tsDateModified": 1699123456,
      "_bHasFiles": true,
      "_aTags": ["tag1", "tag2"],
      "_aPreviewMedia": {
        "_aImages": [
          {
            "_sType": "screenshot",
            "_sBaseUrl": "https://images.gamebanana.com/img/ss/mods",
            "_sFile": "abc123.jpg",
            "_sFile220": "220-90_abc123.jpg"
          }
        ]
      },
      "_aSubmitter": {
        "_idRow": 12345,
        "_sName": "Username",
        "_bIsOnline": true,
        "_sProfileUrl": "https://gamebanana.com/members/12345"
      },
      "_aGame": {
        "_idRow": 4254,
        "_sName": "Counter-Strike 1.6",
        "_sProfileUrl": "https://gamebanana.com/games/4254"
      }
    }
  ]
}
```
