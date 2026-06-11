# Error handling

**Global error handler:**

- Catches:
  - Synchronous thrown errors.
  - Rejected promises in route handlers (via wrapper).
- Logs:
  - Error message
  - Stack trace
  - Request context (method, path, user id if available)

**Client responses:**

All responses use the following consistent shape:

```
{ success: boolean, data?: any, error?: { code, message, details? } }
```

- On success: return `{ success: true, data: ... }`.
- On error: return `{ success: false, error: { code, message, details? } }`.
- Never expose stack traces to clients.

**Common error codes:**

- `400` — validation errors.
- `401` — unauthenticated.
- `403` — unauthorised.
- `404` — not found.
- `500` — unexpected server error.
