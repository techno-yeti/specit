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

- Do not expose stack traces.
- Use consistent shape:
  - `status` — HTTP status code.
  - `body` — `{ success: false, error: { code, message } }`.

**Common codes:**

- `400` — validation errors.
- `401` — unauthenticated.
- `403` — unauthorised.
- `404` — not found.
- `500` — unexpected server error.
