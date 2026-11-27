# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Project

Arcade Vault: an online platform for playing games and competing for the highest score. The project is in its initial state (Create Next App scaffold); no features have been built yet.

Development follows **Spec Driven Design** using the `/spec` and `/spec-impl` skills from https://github.com/Klerith/fernando-skills (install with `npx skills@latest add Klerith/fernando-skills`). Write the spec before implementing a feature.

## Skills
Usa siempre /frontend-design para diseñar la interfaz de usuario.

No test runner is configured yet.

## Stack and non-obvious configuration

- **Next.js 16.4.6 / React 19.3 (App Router, `app/`)**. As AGENTS.md says, APIs differ from older Next.js; the bundled docs live in `node_modules/next/dist/docs/` (`01-app/` for the App Router: getting-started, guides, api-reference). Check them before using Next APIs.
- `next.config.ts` enables `cacheComponents`, `partialPrefetching`, and `experimental.agentFeedback`. With Cache Components on, data fetching and caching follow the `"use cache"` / Suspense model — read the docs on Cache Components before writing data-loading code.
- Route props use the globally generated helper types (e.g. `LayoutProps<"/">`, `PageProps<...>`) instead of hand-written prop types.
- **Tailwind CSS v4** is wired through Turbopack's `@tailwindcss/turbopack` loader for `*.css` in `next.config.ts` — there is no `postcss.config` or `tailwind.config`. Theme tokens are defined in `app/globals.css` via `@theme inline`.
- Import alias `@/*` maps to the repo root.
