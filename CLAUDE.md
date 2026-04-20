# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Local preview

The deployed site is plain HTML/CSS — no build step required. Open any `.html` file directly in a browser, or serve with Python:

```bash
python3 -m http.server 8000
# Then open http://localhost:8000
```

## Deployment

#GitHub Actions (`.github/workflows/deploy.yml`) deploys automatically on push to `main`. It publishes the repository root to `gh-pages`, **excluding** `.github/`, `docs/`, `mkdocs.yml`, `#requirements.txt`, and `site/`. The live site is at `https://bioinfo-kaust.github.io/metagenomics-course/`.

#> The `docs/` directory and `mkdocs.yml` are an older MkDocs scaffold that is **not deployed**. The active site is the root-level HTML files.

## Architecture

The site is a set of hand-authored HTML pages sharing a single stylesheet (`styles.css`) and a shared footer loaded via `<iframe src="footer.html">`.

### Page types

**Top-level pages** (`index.html`, `modules.html`, `schedule.html`, `setup.html`, `resources.html`): Standard pages with `<nav>`, hero or content sections, and a `footer.html` iframe.

**Module pages** (`module-01-qc.html` … `module-08-summary.html`): Each follows a fixed structure:
1. `<nav>` with `.active` on the Modules link
2. `<div class="module-header">` — breadcrumb, module number/day label, `<h1>`, and intro `<p>`
3. `<main>` → `<div class="content-grid">` containing:
   - `<div class="content-body">` — all headings, steps, code blocks, tables, callouts
   - `<aside class="sidebar">` — two `.sidebar-card` blocks: "On This Page" anchor links and "All Modules" nav
4. `<iframe src="footer.html">` footer

### Key CSS classes (styles.css)

| Class | Use |
|---|---|
| `.content-grid` | Two-column layout: `1fr 280px` (collapses to single column on mobile) |
| `.content-body` | Left column; headings auto-get border-top separators |
| `.sidebar` | Right column; sticky within viewport |
| `.module-header` | Dark-blue full-width header bar for module pages |
| `.card-grid` / `.card-grid-3` / `.card-grid-4` | Responsive auto-fit grids for cards |
| `.module-card` | Clickable card linking to a module page |
| `.tool-tag` | Pill badge for tool names |
| `.callout` | Info box; variants: `.callout-note`, `.callout-tip`, `.callout-warning`, `.callout-danger` |
| `.pipeline` / `.pipeline-step` | Vertical pipeline diagram on the home page |
| `section.alt` | Light-grey alternate section background |

All `h2[id]` and `h3[id]` elements get `scroll-margin-top: 80px` to compensate for the sticky nav.

### Copy buttons on code blocks

Every `<pre><code>` block in module pages is wrapped in a `<div style="position:relative;">` with a `<button class="copy-btn" onclick="copyCode(this)">Copy</button>`. The `copyCode()` function is inlined in each module page's `<head>`:

```html
<script>function copyCode(btn){const pre=btn.parentElement.querySelector('code');navigator.clipboard.writeText(pre.innerText);btn.textContent='Copied!';setTimeout(()=>btn.textContent='Copy',2000);}</script>
```

### footer.html

Shared across all pages via iframe. Contains module links, external tool links, and KAUST links. **Update this file whenever modules are renamed or added.**

## Module naming convention

| File | Module | Day |
|---|---|---|
| `module-01-qc.html` | QC & Preprocessing | Day 1 |
| `module-02-assembly.html` | Assembly, Evaluation & Annotation | Day 2 |
| `module-03-ancient-dna.html` | Ancient DNA Analysis | Day 2 |
| `module-04-binning.html` | Contig Binning | Day 3 |
| `module-05-bin-refinement.html` | Bin Refinement | Day 3 |
| `module-06-bin-qc.html` | Bin Quality Evaluation | Day 3 |
| `module-07-taxonomy.html` | Taxonomy & Annotation | Day 4 |
| `module-08-summary.html` | Run Summary | Day 4 |

## When adding a new module page

1. Copy an existing module page as a template.
2. Add it to the `nav ul` in every existing page's `<nav>`.
3. Add a card to `modules.html`.
4. Add it to the sidebar "All Modules" list in every other module page's `<aside>`.
5. Update `footer.html` module list.
6. Update `index.html` pipeline overview and "What You Will Learn" cards.
