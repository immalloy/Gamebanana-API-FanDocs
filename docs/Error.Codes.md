# GameBanana API - Error Codes Reference

> Comprehensive list of error codes returned by the GameBanana APIs

---

## Web API (apiv11) Errors

### Format

```json
{
  "_sErrorCode": "ERROR_CODE",
  "_sErrorMessage": "Human readable message"
}
```

---

## Common Error Codes

### Authentication Errors

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| `AUTH_FAILED` | 401 | Invalid credentials |
| `AUTH_REQUIRED` | 401 | Authentication required |
| `EMAIL_NOT_CONFIRMED` | 401 | Email not yet verified |
| `INVALID_SESSION` | 401 | Session expired or invalid |

### Validation Errors

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| `CONFLICTING_FILTERS` | 400 | Cannot include and exclude same values |
| `INVALID_PARAMETER` | 400 | Invalid parameter value |
| `MISSING_PARAMETER` | 400 | Required parameter missing |
| `INVALID_ITEM_TYPE` | 400 | Invalid item type specified |
| `INVALID_SORT` | 400 | Invalid sort order specified |

### Resource Errors

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| `NOT_FOUND` | 404 | Resource not found |
| `DELETED` | 404 | Resource has been deleted |
| `HIDDEN` | 404 | Resource is hidden |
| `PRIVATE` | 403 | Resource is private |

### Rate Limiting

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| `RATE_LIMITED` | 429 | Too many requests |
| `BOT_DETECTED` | 403 | Automated request detected |

### Submission Errors

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| `ALREADY_LIKED` | 400 | Already liked this item |
| `NOT_LIKED` | 400 | Haven't liked this item |
| `ALREADY_SUBSCRIBED` | 400 | Already subscribed |
| `NOT_SUBSCRIBED` | 400 | Not subscribed |
| `ALREADY_THANKED` | 400 | Already thanked |
| `CANNOT_THANK_SELF` | 400 | Cannot thank your own submission |

---

## Official API Errors

### Format

```xml
<error>
  <code>ERROR_CODE</code>
  <message>Human readable message</message>
</error>
```

Or in JSON:
```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message"
  }
}
```

---

## Common Error Codes

| Error Code | Description |
|------------|-------------|
| `INVALID_ITEMTYPE` | Invalid item type parameter |
| `INVALID_FIELD` | Invalid field requested |
| `INVALID_ID` | Invalid ID provided |
| `ITEM_NOT_FOUND` | Item does not exist |
| `MISSING_APIKEY` | API key required |
| `INVALID_APIKEY` | Invalid API key |
| `RATE_LIMIT_EXCEEDED` | Too many requests |

---

## Handling Errors

### Retry Strategy

```python
import time

def make_request_with_retry(url, max_retries=3):
    for attempt in range(max_retries):
        try:
            response = requests.get(url)
            if response.status_code == 200:
                return response.json()
            elif response.status_code == 429:
                wait_time = 2 ** attempt
                print(f"Rate limited. Waiting {wait_time}s...")
                time.sleep(wait_time)
            else:
                print(f"Error: {response.status_code}")
                return None
        except Exception as e:
            print(f"Exception: {e}")
    return None
```

### Error Response Example

```json
{
  "_sErrorCode": "CONFLICTING_FILTERS",
  "_sErrorMessage": "If you include and exclude the same values the universe will implode"
}
```

---

## Best Practices

1. **Validate inputs** before making requests
2. **Handle rate limits** with exponential backoff
3. **Check HTTP status** before parsing response
4. **Log errors** for debugging
5. **Provide user feedback** on failures
