# Routing specification

**Page routes (server-rendered views):**

- `GET /` — landing page
- `GET /login`
- `GET /register`
- `GET /dashboard` — authenticated

**API routes (JSON under `/api/v1`):**

Defined in `/spec/api/endpoints.md`. All API routes are prefixed with `/api/v1`.

**Conventions:**

- Use `router` modules per domain: `auth.routes`, `user.routes`, etc.
- Prefix API routes with `/api/v1`.
- Protect authenticated routes with auth middleware.
- Return the consistent JSON shape defined in `/spec/api/error-handling.md`.
