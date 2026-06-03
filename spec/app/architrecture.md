# Application architecture

**Stack:**

- **Backend:** Node.js + Express
- **Views:** EJS templates (or similar server-side templating)
- **Database:** MongoDB (via Mongoose)
- **Styling:** TailwindCSS, compiled to a single CSS file
- **API style:** RESTful JSON endpoints under `/api/v1`

**Folder structure (code, not spec):**

- `src/server.ts|js` — Express bootstrap
- `src/config/` — config loaders (env, db, security)
- `src/routes/` — route definitions
- `src/controllers/` — request handlers
- `src/middleware/` — custom middleware
- `src/models/` — Mongoose models
- `src/views/` — EJS templates
- `src/public/` — static assets (compiled CSS, JS)

**Principles:**

- Thin routes, fat controllers.
- No business logic in views.
- All DB access via models/services.
- Centralised error handling and logging.
