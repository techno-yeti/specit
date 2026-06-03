# Routing specification

**Base paths:**

- Public pages:
  - `GET /` — landing page
  - `GET /login`
  - `GET /register`
- Authenticated pages:
  - `GET /dashboard`
- API (JSON):
  - `GET /api/v1/health`
  - `POST /api/v1/auth/login`
  - `POST /api/v1/auth/register`
  - `POST /api/v1/auth/logout`
  - `GET /api/v1/users/me`

**Conventions:**

- Use `router` modules per domain: `auth.routes`, `user.routes`, etc.
- Prefix API routes with `/api/v1`.
- Protect authenticated routes with auth middleware.
- Return consistent JSON shape: `{ success: boolean, data?: any, error?: { code, message, details? } }`.
