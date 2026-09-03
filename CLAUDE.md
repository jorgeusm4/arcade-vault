# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Arcade Vault (`app/`, README in Spanish) — a platform for playing games online and competing for high scores. Currently a freshly scaffolded Next.js app (App Router) with no custom features implemented yet.

## Critical: this Next.js version is not the one you trained on

`AGENTS.md` (imported by this file) warns that this project's Next.js version has breaking changes vs. training data. Before writing any Next.js code, read the relevant guide under `node_modules/next/dist/docs/`:
- `01-app/` — App Router (this project uses App Router: `app/layout.tsx`, `app/page.tsx`)
- `03-architecture/` — compiler, fast refresh, supported browsers
- `04-glossary.md`

Check for deprecation notices before relying on patterns from memory.

## Commands

```bash
npm run dev     # start dev server (Next.js dev, generates AGENTS.md block — see below)
npm run build   # production build
npm run start   # run production build
npm run lint    # eslint (flat config via eslint.config.mjs)
```

There is no test setup yet.

## Architecture

- App Router only (`app/` directory) — `app/layout.tsx` is the root layout, `app/page.tsx` the home page, `app/globals.css` global styles.
- Styling via Tailwind CSS v4 (`@tailwindcss/postcss`).
- TypeScript strict mode; path alias `@/*` maps to the project root (`tsconfig.json`).
- ESLint flat config extends `eslint-config-next` (core-web-vitals + typescript).

## AGENTS.md is auto-managed

The `# This is NOT the Next.js you know` block in `AGENTS.md` is written/re-added by `next dev` (`node_modules/next/dist/server/lib/generate-agent-files.js`). Don't remove it — removing it just re-creates the same uncommitted diff on next dev run. Commit it as-is to keep the tree clean.

## Spec-driven workflow

README states this project follows spec-driven design using `/spec` and `/spec-impl`, based on practices from https://github.com/Klerith/fernando-skills, installed via:

```bash
npx skills@latest add Klerith/fernando-skills
```
