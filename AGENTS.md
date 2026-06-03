# Repository Guidelines

## Project Structure & Module Organization

This repository contains a static HTML presentation. The main artifact is `ai-for-study-and-work.html`, a single self-contained deck with inline CSS and JavaScript. There is currently no `src/`, `tests/`, or build directory. IDE metadata lives in `.idea/` and should not be treated as application source.

If the deck grows, keep related assets in a sibling folder named after the deck, for example `ai-for-study-and-work-assets/`, and reference them with relative paths.

## Build, Test, and Development Commands

No package manager or build system is configured. Open the presentation directly in a browser:

```powershell
Start-Process -FilePath .\ai-for-study-and-work.html
```

For a quick markup search or content audit:

```powershell
Select-String -Path .\ai-for-study-and-work.html -Pattern "section class=`"slide"
```

If future tooling is added, document the exact commands here before relying on them in reviews or automation.

## Coding Style & Naming Conventions

Use plain HTML, CSS, and JavaScript unless a build pipeline is intentionally introduced. Keep the presentation self-contained where practical: inline styles, inline scripts, and fixed 1920x1080 slide layout. Use two-space or four-space indentation consistently within edited sections; the current HTML uses four spaces.

Name presentation files with lowercase kebab-case, for example `ai-for-study-and-work.html`. Keep CSS sections clearly commented with `/* === SECTION NAME === */`.

## Testing Guidelines

There is no automated test framework. Validate changes manually by opening the HTML in a browser and checking:

- slide navigation with arrow keys and Space;
- all 10 slides are reachable;
- no text overflows panels at fullscreen and smaller browser sizes;
- edit mode toggles with `E` and text remains editable.

For structural checks, search for slide sections and confirm only one starts with `class="slide active"`.

## Commit & Pull Request Guidelines

Git history could not be inspected in this sandbox because the repository is not marked as a safe Git directory for the current user. Use concise, imperative commit messages. Conventional Commit style is preferred, for example:

```text
docs: add repository contributor guide
feat: update AI presentation content
fix: correct slide navigation counter
```

Pull requests should include a short summary, screenshots or a screen recording for visual slide changes, and notes about manual browser checks performed.

## Agent-Specific Instructions

Do not introduce npm, bundlers, or external dependencies unless the task requires them. Keep edits scoped to presentation content and supporting documentation. Avoid modifying `.idea/` unless explicitly requested.

After completing any file change or task step, suggest one recommended commit message that matches the actual change. Use Conventional Commit style, for example `docs: update repository guidelines` or `feat: revise presentation landing slide`.
