# Repository Guidelines

## Project Structure & Module Organization

This repository contains a static HTML presentation. The active working deck is `index.html`, a self-contained deck with inline CSS and JavaScript. Supporting source notes live in `docs/`. Previous deck versions live in `versions/` for reference only. There is currently no `src/`, `tests/`, or build output directory. IDE metadata lives in `.idea/` and should not be treated as application source.

If the active deck grows beyond self-contained HTML, keep related assets in a sibling folder named after the deck, for example `index-assets/`, and reference them with relative paths.

## Build, Test, and Development Commands

This project uses `pnpm` for local tooling. No build step is configured; open the presentation directly in a browser:

```powershell
Start-Process -FilePath .\index.html
```

For a quick markup search or content audit:

```powershell
Select-String -Path .\index.html -Pattern "section class=`"slide"
```

Formatting is handled by Prettier:

```powershell
pnpm format
pnpm format:check
```

Playwright is available for browser-based checks:

```powershell
pnpm exec playwright test
```

Do not run Playwright automatically after visual presentation edits unless the user explicitly asks for it. The user will review presentation changes manually and request Playwright checks when needed.

## Coding Style & Naming Conventions

Use plain HTML, CSS, and JavaScript unless a build pipeline is intentionally introduced. Keep the presentation self-contained where practical: inline styles, inline scripts, and fixed 1920x1080 slide layout. Use Prettier defaults for files covered by the formatter, and keep indentation consistent within edited sections when making narrow manual changes.

Name new presentation files with lowercase kebab-case. Keep CSS sections clearly commented with `/* === SECTION NAME === */`.

## Testing Guidelines

Validate presentation changes manually in a browser or with Playwright by checking:

- slide navigation with arrow keys and Space;
- all 10 slides are reachable;
- no text overflows panels at fullscreen and smaller browser sizes;
- edit mode toggles with `E` and text remains editable.

For structural checks, search `index.html` for slide sections and confirm only one slide starts with `class="slide active"`.

## Commit & Pull Request Guidelines

Git history could not be inspected in this sandbox because the repository is not marked as a safe Git directory for the current user. Use concise, imperative commit messages. Conventional Commit style is preferred, for example:

```text
docs: add repository contributor guide
feat: update AI presentation content
fix: correct slide navigation counter
```

Pull requests should include a short summary, screenshots or a screen recording for visual slide changes, and notes about manual browser checks performed.

## Agent-Specific Instructions

Use `pnpm` for project tooling; do not use `npm` or `yarn` for dependency changes unless the user explicitly requests it. Do not introduce bundlers or a build pipeline unless the task requires them. Keep edits scoped to presentation content, supporting documentation, and configured tooling. Avoid modifying `.idea/` unless explicitly requested.

Make presentation changes only in `index.html`. Do not edit files in `versions/`; that directory stores previous versions only for reference, comparison, and recovering ideas from earlier iterations.

When creating, redesigning, or visually rendering presentation layouts, always read and apply `DESIGN.md` first. Treat it as the source of truth for colors, typography, spacing, component style, and overall visual direction unless the user explicitly requests a different design system.

For presentation UI, style tables, repeated list items, prompt parts, and similar content blocks as dark rounded cards matching the established slide card pattern: near-black surface, subtle border, 12px radius, restrained yellow accent, and no large empty wrapper panel behind individual cards unless the layout specifically needs a framed tool.

For `index.html` visual edits, do not launch Playwright or browser automation after completing the change unless the user explicitly requests testing.

After completing any file change or task step, suggest one recommended commit message that matches the actual change. Use Conventional Commit style, for example `docs: update repository guidelines` or `feat: revise presentation landing slide`.
