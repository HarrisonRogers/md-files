# md-files

A personal template for AI coding agent instructions. Copy these files into any project so agents know how you want code organised, named, and structured.

## What this is for

This repo is the single source of truth for my project conventions. Instead of re-explaining preferences in every chat or project, I copy these markdown files into a repo’s root and let the agent pick them up automatically.

The goal is consistent output across projects: same folder layout, naming style, separation of concerns, and workflow expectations — whether the agent is in Cursor, Claude Code, or another tool that reads project instructions.

## Files

| File | Purpose |
|------|---------|
| `AGENTS.md` | Main instructions: structure, naming, components, data, hooks, code quality, and agent workflow. |
| `CLAUDE.md` | Points Claude Code at `AGENTS.md` so both tools share one set of rules. |

Edit `AGENTS.md` here when your preferences change. Other projects stay in sync by copying the updated files in.

## How to use in another project

1. Copy `AGENTS.md` into the project root.
2. Copy `CLAUDE.md` into the project root (if you use Claude Code).
3. Commit them so they travel with the repo and are available to any agent session.

Some tools pick these up automatically from the repo root. In Cursor, they may also be referenced via rules or `@`-mentions depending on your setup.

## What the instructions cover

- **Core principles** — focused files, clear separation of concerns, no premature abstraction
- **Naming** — camelCase for files, folders, and symbols (with framework exceptions)
- **Project structure** — `components/`, `pages/`, `features/`, `data/`, `hooks/`, `lib/`, `services/`, etc.
- **Components** — where page, feature, layout, and UI components live
- **Next.js** — thin route files; real UI in `components/pages/<pageName>/`
- **Functions & utilities** — when to extract vs keep local
- **Data & hooks** — where fetching, constants, and shared hooks belong
- **Code quality** — types, error states, accessibility, avoiding unnecessary dependencies
- **Agent workflow** — read first, match existing patterns, make focused changes

See `AGENTS.md` for the full spec.

## Keeping it updated

When you refine how you want agents to work:

1. Update `AGENTS.md` in this repo.
2. Copy the changed files into projects that should follow the new rules.

Treat this repo as the canonical version; project copies are snapshots you refresh when needed.
