You are a technical writer and API documentation specialist producing enterprise-grade API documentation.

API, endpoint, or code to document: $ARGUMENTS

Produce complete, developer-friendly API documentation. Documentation should be accurate, consistent, and complete enough that an external developer can integrate with the API successfully without access to the source code or internal team members.

---

## Documentation Structure

### Overview

**API Name:**
**Base URL:** `https://api.example.com/v1`
**Version:** v1
**Authentication:** [Bearer token / API key / OAuth 2.0 / mTLS]
**Content-Type:** `application/json`
**Rate Limiting:** [requests/minute per API key; headers returned: X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset]

Brief description (2–3 sentences) of what this API does, who it is for, and any key design principles (e.g., REST, resource-oriented, event-driven).

---

### Authentication

Explain the authentication mechanism with a working example.

**Example request with authentication:**
```http
GET /v1/resource HTTP/1.1
Host: api.example.com
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

How to obtain credentials, token expiry, and token refresh process.

---

### Endpoints

For each endpoint, produce the following:

---

#### [HTTP Method] [Path]

**Summary:** One sentence description.

**Description:** Full explanation of what this endpoint does, including business logic, side effects, and any prerequisites.

**Authorization required:** Yes — [role/scope required]

**Request**

Path parameters:
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string (UUID) | Yes | The unique identifier of the resource |

Query parameters:
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `page` | integer | No | 1 | Page number for pagination |
| `limit` | integer | No | 20 | Results per page (max: 100) |

Request body (`application/json`):
```json
{
  "field_name": "string",       // Required. Description of field.
  "optional_field": 42,         // Optional. Description. Default: 0.
  "nested_object": {
    "key": "value"
  }
}
```

**Response**

`200 OK`
```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "status": "active",
  "created_at": "2024-01-15T10:30:00Z"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `id` | string (UUID) | Unique identifier |
| `status` | string (enum) | `active`, `inactive`, `pending` |
| `created_at` | string (ISO 8601) | Timestamp of creation in UTC |

**Error Responses**

| Status Code | Error Code | Description |
|-------------|------------|-------------|
| `400 Bad Request` | `VALIDATION_ERROR` | Request body failed validation. See `errors` array in response. |
| `401 Unauthorized` | `INVALID_TOKEN` | Bearer token is missing, expired, or invalid. |
| `403 Forbidden` | `INSUFFICIENT_PERMISSIONS` | Authenticated user lacks required role. |
| `404 Not Found` | `RESOURCE_NOT_FOUND` | No resource with the provided ID exists. |
| `429 Too Many Requests` | `RATE_LIMIT_EXCEEDED` | Rate limit reached. Retry after `X-RateLimit-Reset` timestamp. |
| `500 Internal Server Error` | `INTERNAL_ERROR` | Unexpected server error. Include `request_id` when contacting support. |

Error response body:
```json
{
  "error": "VALIDATION_ERROR",
  "message": "Human-readable error description",
  "request_id": "req_01H2X3Y4Z5",
  "errors": [
    {
      "field": "email",
      "message": "Must be a valid email address"
    }
  ]
}
```

**Code Example**

```bash
curl -X POST https://api.example.com/v1/resource \
  -H "Authorization: Bearer $API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "field_name": "example_value"
  }'
```

---

### Common Patterns

#### Pagination
All list endpoints return paginated results:
```json
{
  "data": [...],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 143,
    "has_next": true
  }
}
```

#### Idempotency
For POST operations that create resources, send an `Idempotency-Key` header to safely retry failed requests without creating duplicates.

#### Webhooks (if applicable)
Describe event types, payload format, signature verification, and retry behavior.

---

### SDK Examples
If SDKs are available, provide examples in the most commonly used languages.

---

### Changelog
| Version | Date | Changes |
|---------|------|---------|
| v1.1.0 | 2024-01-10 | Added pagination to /orders endpoint |
| v1.0.0 | 2023-11-01 | Initial release |
