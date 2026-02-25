# JavaScript/Node.js Quick Reference

> Copy-paste code snippets for JS/TS

---

## Setup

```javascript
// Browser or Node.js
const BASE_WEB = "https://gamebanana.com/apiv11";
const BASE_OFFICIAL = "https://api.gamebanana.com";

const headers = {
  "User-Agent": "MyApp/1.0",
  "Accept": "application/json"
};
```

---

## Fetch API

```javascript
// Search mods
async function searchMods(query, gameId = null) {
  const params = new URLSearchParams({
    _sSearchString: query,
    _sModelName: "Mod",
    _nPage: "1",
    _nPerpage: "20"
  });
  if (gameId) params.append("_idGameRow", gameId);
  
  const r = await fetch(`${BASE_WEB}/Util/Search/Results?${params}`);
  return r.json();
}

// Get mod details
async function getMod(modId) {
  const r = await fetch(`${BASE_WEB}/Mod/${modId}/ProfilePage`);
  return r.json();
}

// Get game
async function getGame(gameId) {
  const r = await fetch(`${BASE_WEB}/Game/${gameId}/ProfilePage`);
  return r.json();
}
```

---

## Node.js (with axios)

```javascript
const axios = require("axios");

const client = axios.create({
  baseURL: "https://gamebanana.com/apiv11",
  headers: { "User-Agent": "MyApp/1.0" }
});

// Search
async function searchMods(query, gameId = null) {
  const params = { _sSearchString: query, _sModelName: "Mod" };
  if (gameId) params._idGameRow = gameId;
  const r = await client.get("/Util/Search/Results", { params });
  return r.data;
}

// Get mod
async function getMod(modId) {
  const r = await client.get(`/Mod/${modId}/ProfilePage`);
  return r.data;
}

// Get game with categories
async function getGame(gameId) {
  const r = await client.get(`/Game/${gameId}/ProfilePage`);
  return r.data;
}
```

---

## Lists

```javascript
// Latest mods
async function latestMods(page = 1, perpage = 20) {
  const r = await fetch(
    `${BASE_WEB}/Mod/Index?_nPage=${page}&_nPerpage=${perpage}`
  );
  return r.json();
}

// Game submissions
async function gameSubmissions(gameId, page = 1) {
  const r = await fetch(
    `${BASE_WEB}/Game/${gameId}/Subfeed?_nPage=${page}`
  );
  return r.json();
}

// Featured
async function featured(section = "Mod") {
  const r = await fetch(`${BASE_WEB}/Util/List/Featured?_sModelName=${section}`);
  return r.json();
}
```

---

## Pagination

```javascript
async function fetchAll(url, params = {}) {
  const results = [];
  let page = 1;
  
  while (true) {
    params._nPage = page;
    const r = await fetch(url + "?" + new URLSearchParams(params));
    const data = await r.json();
    
    results.push(...data._aRecords);
    
    if (data._aMetadata._bIsComplete) break;
    page++;
  }
  
  return results;
}

// Usage
const allMods = await fetchAll(
  `${BASE_WEB}/Game/4254/Subfeed`,
  { _nPerpage: 50 }
);
```

---

## Extract Data

```javascript
// Safe extract records
const getRecords = (response) => response?._aRecords ?? [];

// Get key mod info
const getModInfo = (mod) => ({
  id: mod._idRow,
  name: mod._sName,
  views: mod._nViewCount ?? 0,
  downloads: mod._nDownloadCount ?? 0,
  likes: mod._nLikeCount ?? 0,
  tags: mod._aTags ?? [],
  url: mod._sProfileUrl
});

// Usage
const data = await searchMods("weapon");
const mods = getRecords(data).map(getModInfo);
console.log(mods);
```

---

## Rate Limiter

```javascript
class RateLimiter {
  constructor(maxPerSecond = 10) {
    this.minInterval = 1000 / maxPerSecond;
    this.lastRequest = 0;
  }
  
  async wait() {
    const now = Date.now();
    const elapsed = now - this.lastRequest;
    if (elapsed < this.minInterval) {
      await new Promise(r => setTimeout(r, this.minInterval - elapsed));
    }
    this.lastRequest = Date.now();
  }
}

const limiter = new RateLimiter(10);

// Use before requests
async function safeGet(url) {
  await limiter.wait();
  return fetch(url).then(r => r.json());
}
```

---

## Complete Example

```javascript
// Find mods for a game
async function main() {
  const gameId = 4254; // Counter-Strike 1.6
  
  const r = await fetch(
    `${BASE_WEB}/Game/${gameId}/Subfeed?_nPerpage=5`
  );
  const data = await r.json();
  
  console.log(`Found ${data._aMetadata._nRecordCount} mods`);
  
  for (const mod of data._aRecords) {
    console.log(`  - ${mod._sName} (${mod._nDownloadCount ?? 0} downloads)`);
  }
}

main();
```

---

## TypeScript Types

```typescript
interface GBResponse<T = any> {
  _aMetadata: {
    _nRecordCount: number;
    _nPerpage?: number;
    _bIsComplete: boolean;
  };
  _aRecords: T[];
}

interface GBMod {
  _idRow: number;
  _sModelName: string;
  _sName: string;
  _sProfileUrl: string;
  _nViewCount?: number;
  _nDownloadCount?: number;
  _nLikeCount?: number;
  _aTags: string[];
  _aPreviewMedia?: {
    _aImages: GBImage[];
  };
}

interface GBImage {
  _sType: string;
  _sBaseUrl: string;
  _sFile: string;
  _sFile220?: string;
  _sFile530?: string;
}
```
