# SpecIt

A **specification-first** web application blueprint — a complete set of documented design decisions for a MERN-style stack with server-rendered views, ready to be implemented by any capable code-generation agent.

> **Stack:** Node.js + Express | MongoDB (Mongoose) | EJS | TailwindCSS

## Purpose

SpecIt defines _what_ to build, not _how_. The `spec/` directory contains a comprehensive, opinionated set of specifications covering every layer of a modern web application. The companion `agents.md` file acts as a contract for AI-powered code generators, ensuring consistent, secure, and maintainable output.

This approach lets you:

- **Design first** — settle architecture, routes, and data models before writing code
- **Generate consistently** — any agent following the spec produces the same app
- **Audit and iterate** — changes start as spec edits, not scattered code hunts

## What's Inside

### Specifications (`spec/`)

| Area               | Files         | Covers                                                                        |
| ------------------ | ------------- | ----------------------------------------------------------------------------- |
| **Application**    | `app/`        | Architecture, environment config, logging, middleware, routing, security      |
| **API**            | `api/`        | REST endpoints, error handling, request validation                            |
| **Authentication** | `auth/`       | Registration/login/logout flows, JWT/session strategy, role-based permissions |
| **Database**       | `database/`   | MongoDB schemas, query patterns, migrations                                   |
| **Frontend**       | `frontend/`   | EJS layout, TailwindCSS setup, reusable components, forms, accessibility      |
| **Deployment**     | `deployment/` | Docker, CI/CD pipeline, production runtime                                    |
| **Testing**        | `testing/`    | Unit, integration, and end-to-end testing strategies                          |

### Generator Contract (`agents.md`)

The `agents.md` file is a machine-readable contract that governs how a code-generation agent should produce the application. It includes:

- **General rules** — stack constraints, output folder structure, code style
- **Security rules** — mandatory protections (Helmet, CSP, bcrypt, rate limiting, input sanitisation)
- **Authentication rules** — login, registration, logout, role-based access
- **Database rules** — Mongoose models, indexes, lean queries, injection prevention
- **API rules** — endpoint implementation, validation, consistent JSON responses
- **Frontend rules** — EJS templates, Tailwind utilities, accessibility, no client-side frameworks
- **Build & deployment rules** — Tailwind pipeline, Docker, CI/CD
- **Testing rules** — unit, integration, and E2E test requirements
- **Conflict resolution** — priority order when specs disagree

## Key Design Decisions

- **No client-side framework** — server-rendered views with EJS, keeping the frontend lightweight and secure
- **Security-first** — Helmet, CSP, bcrypt, rate limiting, input sanitisation, and secure cookies are mandatory defaults
- **RESTful API** — JSON endpoints under `/api/v1` for any client-side interactivity
- **MongoDB with Mongoose** — schemas with validation, lean queries, TTL indexes
- **TailwindCSS** — compiled via PostCSS into a single static CSS file; no inline styles
- **Cookie-based auth** — session or JWT in `httpOnly`, `secure`, `sameSite` cookies
- **Docker-ready** — multi-stage build, non-root user, environment-variable configuration

## How to Use

1. **Read the specs** — start with `spec/README.md`, then dive into any area of interest.
2. **Hand to an agent** — provide `agents.md` and the full `spec/` directory to an AI code generator. The contract tells it exactly what to build and how.
3. **Iterate on specs** — change a `.md` file and regenerate. No hunting through source code to find the right place.

## Quick Reference: Directory Layout (Generated)

Once the app is generated, the code will follow this structure:

```
src/
├── server.js          — Express bootstrap
├── config/            — env, DB, and security config loaders
├── controllers/       — request handlers
├── middleware/         — auth, validation, error handling
├── models/            — Mongoose schemas
├── routes/            — domain-based route modules
├── services/          — business logic
├── views/             — EJS templates
└── public/            — compiled CSS, static assets
```

## License

MIT License

Copyright (c) 2026 Julian Moors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
