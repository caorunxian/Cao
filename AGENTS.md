# AGENTS.md

## What this repo is

Static HTML/CSS course exercises for the 高级网页设计 (advanced web design) class. No package manager, no build, no lint/test/typecheck, no framework — pages are opened directly in a browser (or any static file server). Nothing to install or run.

## Key file: `index.html`

`index.html` is the portal page: a grid of `.cao_work` card links, one per exercise, plus the assignment brief in a `<blockquote>` (brief requires: native code only, no CDN, page named `index.html`, must link every page in the directory).

- Adding a new exercise page? Also add a matching `<a class="cao_work">` card in `index.html`, or it will not be reachable.
- Known gap: `10-1-animation.html`, `10-2.html`, `10-3.html`, `10-4.html` exist but are not linked from `index.html`. Fix this if asked to sync the index.
- All of `index.html`'s CSS is inline in a single `<style>` block (CSS custom properties on `:root`); there is no shared stylesheet for it.

## Conventions and gotchas

- **Naming rule (important):** all CSS class names, id names, and JS variable names must start with the `cao_` prefix (e.g. `.cao_work`, `#cao_box`, `cao_myVar`). This has already been applied across every existing page. Follow this prefix for any new or edited markup, styles, and scripts.
- Prompt log: every user prompt is appended (never overwritten) to `cao prompt.md` before execution, recording the timestamp, the model used, and the prompt content.
- Each exercise page is self-contained with its own inline `<style>` block. The only external stylesheet is `css.css`, used solely by `5-1层叠与继承.html` — do not assume pages share styles.
- Filenames matter: names mix Chinese and English, and some contain spaces (e.g. `4-1 css.html`, `8-1 css选择器.html`, `5-1层叠与继承.html`). Links in `index.html` reference them verbatim — preserve exact names when creating or linking files; do not rename or URL-encode differently than existing links do.
- Images are referenced relatively from the repo root (`1.png` ~8.5 MB, `2.jpg`, `3.jpg`). Keep new assets in the root.
- Content and UI copy are in Chinese (`lang="zh-CN"`). Match existing Chinese terminology when editing text.
- Some pages intentionally demonstrate a specific technique (transition, animation, flex, selectors). Check whether the page's point is that technique before refactoring it away.
