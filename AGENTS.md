# AGENTS.md

## What this repo is

Static HTML/CSS course exercises for the 高级网页设计 (advanced web design) class. No package manager, no build, no lint/test/typecheck, no framework — pages are opened directly in a browser (or any static file server). Nothing to install or run.

## Key file: `index.html`

`index.html` is the portal page: a grid of `.crx_work` card links, one per exercise, plus the assignment brief in a `<blockquote>` (brief requires: native code only, no CDN, page named `index.html`, must link every page in the directory).

- Adding a new exercise page? Also add a matching `<a class="crx_work">` card in `index.html`, or it will not be reachable.
- Known gap: `10-1-animation.html`, `10-2.html`, `10-3.html`, `10-4.html` exist but are not linked from `index.html`. Fix this if asked to sync the index.
- All of `index.html`'s CSS is inline in a single `<style>` block (CSS custom properties on `:root`); there is no shared stylesheet for it.

## Conventions and gotchas

- **Naming rule (important):** all CSS class names, id names, and JS variable names must start with the `crx_` prefix (e.g. `.crx_work`, `#crx_box`, `crx_myVar`). Follow this prefix for any new or edited markup, styles, and scripts.
- **HTML page header comment (important):** every HTML page must include a comment block at the top of the `<body>` (or right after `<body>`) with the author name, creation date, AI model used, and function name, in this exact format:

  ```html
  <!-- 姓名：曹润贤，建立时间：YYYY-MM-DD，使用大模型：<模型名>，功能名称：<页面功能描述> -->
  ```

  When creating or editing any HTML file, ensure this comment is present. Use today's date as 建立时间 and the name of the AI model that generates the code (e.g. `GLM-5.3-Flash`).
- **Pure native code only (important):** use only native HTML, CSS, and JavaScript. No frameworks, no build tools, no npm packages, no preprocessors. Write plain `<style>` and `<script>` blocks — no external bundlers or transpilers.
- **No third-party libraries or CDN (important):** do NOT import or reference any external library, CSS framework, or CDN (e.g. no Bootstrap, no jQuery, no Vue/React, no Font Awesome CDN, no lucide CDN, no unpkg/jsdelivr etc.). All dependencies must be local files already present in the repo.
- **Icons — use local iconfont only (important):** all icons on every page must use the local iconfont files under `font/`:
  - CSS: `font/iconfont.css`
  - Font files: `font/iconfont.woff`, `font/iconfont.woff2`, `font/iconfont.ttf`
  - Usage: `<link rel="stylesheet" href="font/iconfont.css">`, then `<i class="iconfont icon-xxx"></i>`
  - Do NOT use Font Awesome CDN, lucide CDN, emoji as icons, or any other icon source. Add new icon classes to `iconfont.css` only when absolutely necessary — prefer reusing existing classes.
- **Fetch for server data (important):** whenever a page needs to read data from a server/API, use the native `fetch()` API. Do NOT use `XMLHttpRequest`, jQuery AJAX, axios, or any other HTTP client. Example pattern:

  ```javascript
  fetch('/api/endpoint')
      .then(function (crx_res) { return crx_res.json(); })
      .then(function (crx_data) { /* render */ })
      .catch(function (crx_err) { /* handle error */ });
  ```

- Prompt log: every user prompt is appended (never overwritten) to `cao prompt.md` before execution, recording the timestamp, the model used, and the prompt content.
- Each exercise page is self-contained with its own inline `<style>` block. The only external stylesheet is `css.css`, used solely by `5-1层叠与继承.html` — do not assume pages share styles.
- Filenames matter: names mix Chinese and English, and some contain spaces (e.g. `4-1 css.html`, `8-1 css选择器.html`, `5-1层叠与继承.html`). Links in `index.html` reference them verbatim — preserve exact names when creating or linking files; do not rename or URL-encode differently than existing links do.
- Images are referenced relatively from the repo root (`1.png` ~8.5 MB, `2.jpg`, `3.jpg`). Keep new assets in the root.
- Content and UI copy are in Chinese (`lang="zh-CN"`). Match existing Chinese terminology when editing text.
- Some pages intentionally demonstrate a specific technique (transition, animation, flex, selectors). Check whether the page's point is that technique before refactoring it away.
