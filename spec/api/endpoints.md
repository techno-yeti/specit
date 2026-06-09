# API endpoints

Base path: `/api/v1`

## Health

- `GET /api/v1/health`
  - Response: `{ success: true, data: { status: 'ok' } }`

## Auth

- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`
- `POST /api/v1/auth/logout`
- Optional:
  - `POST /api/v1/auth/password/forgot`
  - `POST /api/v1/auth/password/reset`

## User

- `GET /api/v1/users/me`
  - Auth required.
  - Returns current user profile (no password fields).

All responses follow the shared format defined in `error-handling.md`.
