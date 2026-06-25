# Research Vault

Personal research notebook built with [Quartz](https://quartz.jzhao.xyz/) and deployed to GitHub Pages.

## Live site

**https://stinkydog1501.github.io/research-vault/**

## How it works

- Notes live in `content/` as plain Markdown.
- Push to `main` → GitHub Actions runs `npx quartz build` → publishes to GitHub Pages.
- Full-text search, backlinks, and Obsidian-style `[[wiki-links]]` all work in the published site.

## Local development

```bash
npm install
npx quartz plugin install
npx quartz build --serve   # preview at http://localhost:8080
```

## Adding a note

Drop a `.md` file into `content/` (or any subfolder), commit, and push:

```bash
git add content/
git commit -m "research: <topic>"
git push
```

The site rebuilds automatically within ~1 minute.

## Folders

- `content/index.md` — homepage
- `content/research/` — research notes
- `content/inbox/` — quick captures
- `content/reference/` — durable reference