# AGENTS.md — SK COMPUTER Customer Portal

## What this is
A single static `index.html` page (no build step, no framework). It is a customer
portal & management UI for "SK COMPUTER" written in Marathi (`lang="mr"`).

## Backend
Firebase (hosted SaaS) — Auth, Firestore, Storage — loaded via ESM from the
gstatic CDN. The Firebase config (apiKey, projectId, etc.) is embedded directly
in `index.html`. These are **public client-side keys** by design; access is
controlled by Firebase security rules, not by the API key. No server-side
credentials or local database are needed to run the app.

## Running here
`docker compose -f docker-compose.base44.yml up -d` — nginx:alpine serves the
repo on host port 3000 with the source bind-mounted read-only.

## Editing
There is no live-reload dev server (pure static file). After editing `index.html`,
call `reload_preview` so the preview iframe picks up the change.

## Deployment (repo's own flow)
GitHub Pages via `.github/workflows/static.yml` (deploys the whole repo on push to
`main`). CodeQL analysis runs via `.github/workflows/codeql.yml`.
