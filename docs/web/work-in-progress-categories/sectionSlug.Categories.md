# GET /:sectionSlug/Categories

**Multiple RootCategories**

Returns a list of the root categories by Section Slug.

## Path Variables

| Variable | Description |
|----------|-------------|
| `sectionSlug` | Required. Section slug. |

## Query Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `_sSort` | Yes | Required. String. How to sort the results.   Allowed values: a_to_z, count  Default value: - |
| `_bShowEmpty` | No | Boolean. If provided, include empty categories.  Allowed values: true, false  Default value: - |
| `_idGameRow` | No | [oneOf] Integer. Categories for the specific Game. |
| `_idCategoryRow` | No | [oneOf] Integer. Categories for the specific Category. |

