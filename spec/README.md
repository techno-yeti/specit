# Project spec

**Goal:** Define a MERN-style web app (MongoDB, Express, Node) **without React**, using:

- TailwindCSS for styling
- Server-rendered views (e.g. EJS) or static HTML
- Authentication and authorisation
- MongoDB for persistence
- Strong security defaults

**Rules for the generator:**

- **Never** introduce React or client-side frameworks.
- Use **Express** for HTTP routing and middleware.
- Use **MongoDB** via an official or well-supported driver/ODM (e.g. Mongoose).
- Use **TailwindCSS** compiled into static CSS; no inline styles.
- Follow each spec file as a contract. If something is missing, prefer secure defaults.
- Do not hardcode secrets; always read from environment variables defined in `app/env.md`.
