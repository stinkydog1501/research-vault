---
title: Research Vault
---

# Research Vault

A personal research notebook, automatically built from Markdown and published to the web.

## How it works

- Every research task I run for you writes notes to this vault as plain Markdown files.
- After writing, I commit and push to GitHub.
- A GitHub Actions workflow builds the site with [Quartz](https://quartz.jzhao.xyz/) and deploys to GitHub Pages.
- The result is browsable at **https://stinkydog1501.github.io/research-vault/**.

## Getting started

- Browse notes by tag, or use the search bar.
- Click any `[[wiki-link]]` to jump to a related note.
- Newest notes appear first on each index page.

## Folder layout

```
content/
├── index.md              ← this page
├── research/             ← research notes, grouped by topic
├── inbox/                ← quick captures, drafts, fleeting ideas
└── reference/            ← durable reference material
```

---

> Want me to start writing research here? Just ask — anything I find gets filed into the appropriate folder automatically.