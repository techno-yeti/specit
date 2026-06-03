# Request validation

**Library:** Use a schema-based validator (e.g. Joi, Zod, or similar).

**Patterns:**

- Define schemas per endpoint:
  - `AuthRegisterSchema`
  - `AuthLoginSchema`
  - `PasswordResetRequestSchema`
- Middleware `validate(schema)`:
  - Validates `req.body` (and optionally `req.query`, `req.params`).
  - On failure, respond with `400 Bad Request` and structured error details.

**Rules:**

- Enforce minimum password length and complexity.
- Normalise and validate email addresses.
- Reject unknown fields where appropriate.
