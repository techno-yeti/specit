# Generator Contract

This contract defines the mandatory rules and behaviours that ANY code‑generation agent must follow when producing the application described in the `/spec` directory. It ensures consistency, security, and maintainability across all generated code.

If any spec file contradicts this contract, the contract takes priority unless the spec explicitly overrides it.

---

# 1. General Rules

1. The generator MUST read all `.md` files under `/spec/**` before generating code.
2. The generator MUST follow the structure, conventions, and requirements defined in those files.
3. The generator MUST NOT introduce:
   - React
   - Vue
   - Angular
   - Client-side frameworks
   - Inline JavaScript in HTML
4. The generator MUST produce a **Node.js + Express** backend.
5. The generator MUST produce **server-rendered pages** using EJS (or the templating engine defined in `/spec/frontend/layout.md`).
6. The generator MUST use **TailwindCSS** compiled into a single CSS file.
7. The generator MUST use **MongoDB** via Mongoose.
8. The generator MUST implement authentication exactly as defined in `/spec/auth/**`.
9. The generator MUST implement all security requirements in `/spec/app/security.md`.

---

# 2. Output Structure

The generator MUST create the following folder structure:

/src
/config
/controllers
/middleware
/models
/routes
/services
/views
/public
/css
/js

Code

The generator MUST NOT create additional top-level folders unless explicitly required by a spec file.

---

# 3. Code Style Rules

1. Use modern JavaScript (ES modules or CommonJS depending on spec).
2. Use async/await for all asynchronous operations.
3. No unused variables, dead code, or commented-out blocks.
4. No console logs in production code except where explicitly allowed in `logging.md`.
5. All functions must be pure unless interacting with:
   - Database
   - Filesystem
   - Network
   - Framework APIs

---

# 4. Security Rules (Mandatory)

The generator MUST implement:

- Helmet with CSP
- Rate limiting
- Sanitisation of all user input
- bcrypt password hashing
- Secure cookies (`httpOnly`, `secure`, `sameSite`)
- No inline `<script>` tags
- No inline event handlers (`onclick`, `onchange`, etc.)
- No user-controlled data rendered unsanitised

If any spec file is ambiguous, the generator MUST choose the **most secure** interpretation.

---

# 5. Authentication Rules

The generator MUST:

- Implement login, registration, logout
- Use sessions OR JWT-in-cookie (as defined in `/spec/auth/strategy.md`)
- Protect authenticated routes using middleware
- Implement role-based access control if defined in `/spec/auth/permissions.md`
- Never expose password hashes or sensitive fields

---

# 6. Database Rules

The generator MUST:

- Use Mongoose models defined in `/spec/database/schema.md`
- Apply indexes exactly as defined
- Use lean queries for read-only operations
- Prevent MongoDB operator injection
- Use a test database for integration tests

---

# 7. API Rules

The generator MUST:

- Implement all endpoints in `/spec/api/endpoints.md`
- Validate all requests using schemas in `/spec/api/validation.md`
- Use the global error handler defined in `/spec/api/error-handling.md`
- Return JSON in the shape:

{ success: boolean, data?: any, error?: { code, message, details? } }

Code

---

# 8. Frontend Rules

The generator MUST:

- Use EJS templates
- Use Tailwind utility classes
- Follow layout rules in `/spec/frontend/layout.md`
- Implement components from `/spec/frontend/components.md`
- Implement forms from `/spec/frontend/forms.md`
- Follow accessibility rules from `/spec/frontend/accessibility.md`

The generator MUST NOT:

- Use inline styles
- Use client-side frameworks
- Use uncompiled Tailwind in production

---

# 9. Build Rules

The generator MUST:

- Produce a Tailwind build pipeline (PostCSS)
- Output compiled CSS to `/src/public/css/app.css`
- Minify CSS in production
- Use environment variables defined in `/spec/app/env.md`

---

# 10. Deployment Rules

The generator MUST:

- Produce a Dockerfile matching `/spec/deployment/docker.md`
- Produce CI/CD config matching `/spec/deployment/ci-cd.md`
- Produce production server behaviour matching `/spec/deployment/production.md`

---

# 11. Testing Rules

The generator MUST:

- Implement unit tests for helpers and validation
- Implement integration tests for API endpoints
- Implement E2E tests for full user flows
- Use a test database
- Never run tests against production

---

# 12. Behaviour When Specs Are Missing or Ambiguous

If a spec file is missing:

- The generator MUST choose the **most secure** and **most maintainable** default.

If a spec is ambiguous:

- The generator MUST choose the **simplest** implementation that satisfies:
  1. Security
  2. Maintainability
  3. Consistency with other spec files

If two specs conflict:

Priority order:

security.md
auth/*
api/*
database/*
frontend/*
deployment/*
testing/*
architecture.md

Code

---

# 13. Behaviour When Generating Files

The generator MUST:

- Create files only where required by the spec
- Overwrite files only when explicitly instructed
- Never generate placeholder code unless the spec allows it
- Never invent new features or endpoints

---

# 14. Behaviour When Updating Existing Code

When updating code, the generator MUST:

- Preserve existing functionality unless the spec contradicts it
- Preserve security features
- Preserve environment variable usage
- Preserve folder structure
- Apply minimal changes required to satisfy the updated spec

---

# 15. Completion Criteria

The generator MUST consider the project complete when:

- All spec files have been implemented
- All required folders and files exist
- All tests pass
- The app runs in development mode
- The app builds for production
- The Docker image builds successfully
