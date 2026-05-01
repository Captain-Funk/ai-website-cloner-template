@AGENTS.md

## What This Repo Does

Clones any website into a clean, modern Next.js codebase using AI coding agents. The tool scrapes a live site, extracts its structure and styling, and reconstructs it as an editable Next.js + Tailwind + shadcn/ui project. Used in CAPTAIN for client-site analysis and rapid prototyping inside The War Room.

## CAPTAIN Ecosystem Context

> Forked from [JCodesMore/ai-website-cloner-template](https://github.com/JCodesMore/ai-website-cloner-template). Customized for CAPTAIN.

- **Team:** The Forge (business tooling)
- **Project:** The War Room — business operations, client site analysis
- **Config key:** `cloner` in `~/.claude/captain.config.json`
- **Category:** tool (forked third-party)

## Cross-Repo Rules

- **Reference but not update.** When working in this repo, you can READ from other CAPTAIN repos via captain.config.json. Never WRITE to another repo from a session focused here.
- **Branch strategy:** `master` stays synced with upstream via rebase. All CAPTAIN customizations go on the `captain` branch.
- **After fresh clone:** Run `bash ~/Projects/captain-plugin/hooks/bootstrap.sh` to restore hookify symlinks.

## Upstream Tracking

- **Upstream:** https://github.com/JCodesMore/ai-website-cloner-template.git
- **Sync:** `git fetch upstream && git checkout master && git rebase upstream/master && git checkout captain && git rebase master`

## Stack & Conventions

- **Framework:** Next.js (TypeScript, App Router). See `next.config.ts`.
- **Styling:** Tailwind CSS + shadcn/ui components (`components.json` configures generators).
- **Linting:** flat-config ESLint via `eslint.config.mjs`. Run `pnpm lint` (or `npm run lint`) before committing.
- **Container:** Dockerfile + Dockerfile.dev provided. `docker-compose.yml` orchestrates dev environment.
- **Source layout:** application code in `src/`, generated/scraped output in `public/`, scripts under `scripts/`, docs in `docs/`.

## Common Commands

- `npm run dev` — local Next.js dev server (HMR).
- `npm run build` — production build.
- `npm run lint` — ESLint check.
- `npm run start` — serve the production build.
- `docker compose up dev` — run inside the dev container (matches CI env).
- See `scripts/` for cloning/scraping utilities specific to this tool.

## Gotchas

- **Don't commit on `master`.** Master mirrors upstream and gets rebased. CAPTAIN-specific work belongs on `captain`.
- **`.claude/` is bootstrap output.** Symlinks regenerate via `bootstrap.sh`. Don't hand-edit hookify rules here — edit them in the captain-plugin or Dillons Project source-of-truth.
- **Rebases on `captain` will rewrite history.** Force-pushes are expected after upstream syncs; don't share long-lived branches off `captain`.
- **`bootstrap-audit.log` is gitignored.** It's regenerated each bootstrap run.
- **Default branch is `captain`** (renamed from upstream's `main`/`master`). GitHub PRs target `captain`, not `main`.

## When Working Here

- For scraping/clone logic changes → keep CAPTAIN-specific tweaks isolated so upstream rebases stay clean.
- For workflow/agent changes → prefer pulling shared rules from the captain-plugin instead of hardcoding here.
- Output of clone runs is throwaway code — don't commit generated `public/` artifacts unless they're a deliberate template.
