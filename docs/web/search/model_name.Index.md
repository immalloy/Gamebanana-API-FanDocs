# GET /:model_name/Index

**Latest (section)**

This endpoint returns a list of records matching the given criteria.

## Path Variables

| Variable | Description |
|----------|-------------|
| `model_name` | Required. Enter the model name. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_nPage` | No | Which 'page' of results to get.  Allowed values: greater than 1.  Default value: 1 |
| `_nPerpage` | No | Number of results per page.  Allowed values: 1 through 50.  Default value: 20 |
| `_sSort` | No | How to sort results.  Allowed values: see _aSorts in ListFilterConfig |
| `_aFilters[Generic_WasFeatured]` | No | If provided, display only featured records.  See other filters in ListFilterConfig  Allowed values: true |

