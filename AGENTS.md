# Project Instructions

These instructions apply to all projects in this workspace. Keep codebases clean, separated by concern, and easy to navigate. Prefer obvious structure over clever abstraction.

## Core Principles

- Keep files focused. A file should have one clear job.
- Separate concerns aggressively, but do not split code just to create more files.
- Prefer readable, direct code over unnecessary abstraction.
- Use camelCase for naming conventions across files, folders, variables, functions, hooks, utilities, and feature/page directories unless the framework requires a specific filename.
- Do not create exported helper functions, utility files, or shared modules for logic that is only used once.
- If logic is used once and belongs to one component or page, keep it local to that file or folder.
- Extract shared logic only when it is reused, materially improves clarity, or matches an existing project pattern.
- Keep presentation, data access, business logic, constants, hooks, and framework routing in separate places.
- Follow the existing code style and project conventions before introducing new patterns.

## Naming Conventions

- Use camelCase for file names, folder names, functions, variables, hooks, utilities, services, constants modules, and feature names.
- Prefer `homePage.tsx`, `heroSection.tsx`, `recentProjects.tsx`, `userService.ts`, `projectData.ts`, and `formatDate.ts`.
- Avoid kebab-case, snake_case, and PascalCase filenames unless an existing project convention or framework requirement makes them necessary.
- Framework-required route files are allowed to keep their required names, such as `page.tsx`, `layout.tsx`, `loading.tsx`, `error.tsx`, and `route.ts`.
- React component exports may still use PascalCase because JSX requires component identifiers to be capitalized.
- Type and interface names may use PascalCase when that matches TypeScript conventions.

## Preferred Structure

Use this shape as the default for app projects:

```text
src/
  app/ or pages/
    routeFilesOnly
  components/
    ui/
    layout/
    pages/
      home/
      about/
      dashboard/
    features/
      featureName/
  data/
  hooks/
  lib/
  services/
  styles/
  types/
  utils/
```

Adjust names to match the framework, but keep the separation clear.

## Components

- Components belong in `components/`, not mixed into data, services, or utility folders.
- Page-specific components should live under `components/pages/<pageName>/`.
- Feature-specific components should live under `components/features/<featureName>/`.
- Reusable primitive components should live under `components/ui/`.
- Layout components should live under `components/layout/`.
- A component file should mainly contain rendering logic and small local helpers that directly support that rendering.
- Avoid putting API calls, data normalization, business rules, or large constants directly inside components.

## Page Components

- Page-level components may be declared in the page layer when the framework or project pattern expects that.
- Otherwise, prefer `components/pages/<pageName>/` for page-specific UI.
- For Next.js App Router projects, keep `app/` route folders thin.
- A Next.js `page.tsx` should usually import and render a page component from `components/pages/<pageName>/`.
- Do not place large page implementations, nested components, reusable helpers, data modules, or business logic directly inside `app/` route files.
- Route files should handle routing concerns and delegate real UI and logic to the appropriate folders.

Example:

```tsx
// src/app/page.tsx
import { HomePage } from "@/components/pages/home/homePage";

export default function Page() {
  return <HomePage />;
}
```

## Functions And Utilities

- Shared functions should live outside components, usually in `lib/`, `utils/`, `services/`, or a feature folder.
- Use `utils/` for small generic helpers.
- Use `lib/` for project-level logic and integrations.
- Use `services/` for API clients, persistence, and external service boundaries.
- Use feature folders for logic that belongs to one feature but is shared inside that feature.
- Do not create a helper file for a one-line or one-use function.
- Do not export a function unless another module actually needs it.
- Keep private helper functions close to the code that uses them.

## Data

- Keep static data, seed data, fixtures, and content collections in `data/`.
- Keep API fetching and external data access in `services/` or `lib/`, not in UI components.
- Keep data transformation separate from rendering when transformation is non-trivial.
- Keep constants close to their domain. Use a shared constants file only for values used across multiple areas.

## Hooks

- Shared React hooks should live in `hooks/`.
- Feature-specific hooks may live in the relevant feature folder.
- Do not create a custom hook for state that is simple and used once in one component.
- Hooks should not silently mix unrelated concerns.

## File Size And Organization

- Avoid giant files that combine routing, state, UI, data fetching, helpers, and constants.
- Split files when a section has a distinct responsibility or is likely to be reused.
- Avoid tiny fragmentation where every minor expression becomes a new module.
- Prefer folders with an obvious entry file when a feature or page has multiple parts.

Example:

```text
components/pages/home/
  homePage.tsx
  heroSection.tsx
  recentProjects.tsx
  homeTypes.ts
  homeConstants.ts
```

## Code Quality

- Use descriptive names for files, functions, components, props, and variables.
- Keep functions small enough to understand without jumping around.
- Remove dead code, unused exports, commented-out code, and unused dependencies.
- Prefer explicit types at module boundaries.
- Handle loading, empty, and error states where the UI depends on async data.
- Keep accessibility in mind for interactive components.
- Keep styling consistent with the existing design system or project style.
- Do not introduce a new library, state manager, or abstraction unless it is justified by the problem.

## Agent Workflow

- Read the existing structure before editing.
- Match local naming, formatting, and architectural patterns.
- Make focused changes that solve the current request.
- Do not move unrelated files or perform broad refactors unless asked.
- Preserve user changes and do not overwrite work you did not create.
- When adding code, place it in the folder that matches its responsibility.
- When unsure whether to extract something, prefer local code first and extract after reuse or clear complexity appears.
