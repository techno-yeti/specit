# Docker specification

**Goals:**

- Small, production-ready image.
- Multi-stage build.

**Pattern:**

1. **Builder stage:**
   - Install dependencies.
   - Build Tailwind CSS and any compiled assets.
2. **Runtime stage:**
   - Copy built app and `node_modules` (or use `npm ci --only=production`).
   - Run as non-root user.
   - Expose `PORT`.

**Environment:**

- All configuration via environment variables.
- No secrets baked into the image.
