# Repository Guidelines

## Project Structure & Module Organization
- `index.html` holds the frontend UI and client-side logic.
- `api/worker.ts` is the Cloudflare Worker API (TypeScript) that handles reports, KV storage, and HTML responses.
- `sw.js`, `manifest.json`, and `icon-192.svg` support PWA behavior and assets.
- `wrangler.toml` configures the Worker entrypoint and KV bindings.

## Build, Test, and Development Commands
- `npm install` (or `bun install`) installs dependencies.
- `npm run dev` runs the Worker locally via Wrangler for development and API testing.
- `npm run deploy:api` deploys the Worker to Cloudflare.
- `npm run deploy:pages` deploys the static site to Cloudflare Pages (`fixstreet` project).

## Coding Style & Naming Conventions
- TypeScript is used for the Worker; keep 2-space indentation and semicolons.
- Prefer double quotes for strings to match existing files.
- Use `camelCase` for variables/functions and `SCREAMING_SNAKE_CASE` for constants.
- Keep filenames lowercase when possible; existing assets use short, simple names (e.g., `sw.js`, `icon-192.svg`).

## Testing Guidelines
- No automated test framework is configured yet.
- Before submitting changes, do a manual smoke test:
  - Run `npm run dev`, load the UI, and submit a sample report.
  - Verify `/health` returns JSON and image/report routes respond.
- If you add tests, document the runner and add scripts in `package.json`.

## Commit & Pull Request Guidelines
- Follow Conventional Commits found in history: `feat: ...`, `fix: ...`, `test: ...`.
- Keep commits scoped and descriptive (one change per commit when possible).
- PRs should include: a clear summary, steps to verify, and screenshots for UI changes.
- Link related issues or notes about deployment changes when relevant.

## Configuration & Deployment Notes
- `wrangler.toml` defines the Worker name, entrypoint, and KV namespace binding `REPORTS`.
- Ensure your Cloudflare account has the configured KV namespace before deploying.
