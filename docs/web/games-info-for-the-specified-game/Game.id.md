# GET /Game/:id

**Multiple Properties (2)**

This endpoint returns multiple properties for the specified Game ID.

## Path Variables

| Variable | Description |
|----------|-------------|
| `id` | Required. Integer. Game ID. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_csvProperties` | Yes | String. Comma-separated list of properties to request. Allowed values: see response body. Default value: - |

