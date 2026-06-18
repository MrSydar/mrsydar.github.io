# Agent Context

This is a Hugo static site using the PaperMod theme.

## Theme

- **Theme**: [hugo-PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **Installed via**: Git submodule at `themes/PaperMod`
- **Wiki docs**: https://github.com/adityatelange/hugo-PaperMod/wiki
- **Example site source**: https://github.com/adityatelange/hugo-PaperMod/tree/exampleSite
- **baseURL**: `https://mrsydar.dev/`

## Project Structure

```
.
├── archetypes/
├── assets/
├── content/          # Pages and posts go here
├── data/
├── hugo.yaml         # Site configuration
├── i18n/
├── layouts/
├── static/
└── themes/PaperMod   # Theme (git submodule)
```

## Configuration

Site config is `hugo.yaml` (root level).

- `baseURL`: `https://mrsydar.dev/`
- `title`: site title
- `theme`: `["PaperMod"]` -- theme name
- `pagination.pagerSize`: posts per page (e.g. `5`)
- `enableRobotsTXT`: `true`
- `buildDrafts`: `false`
- `pygmentsUseClasses`: `true`
- `mainsections`: list of content sections shown on homepage, e.g. `["posts"]`
- `menu.main`: navigation entries with `name`, `url`, `weight`
- `outputs.home`: include `[HTML, RSS, JSON]` — JSON is required for search to work
- `params.homeInfoParams`: homepage intro block with `Title` and `Content`
- `params.socialIcons`: list of `{name, url}` for homepage footer

## Homepage Customization

The homepage shows an intro section (`homeInfoParams`) + list of recent posts + social icons.

- **Avatar**: `static/me.jpg` (240×240) is displayed as a circular image above the intro text via a custom `layouts/partials/home_info.html` override.
- **Social icons**: Configured in `hugo.yaml` under `params.socialIcons`. PaperMod supports a built-in set of icons by name.

## Overriding Theme Files

PaperMod loads partials from `layouts/` before falling back to `themes/PaperMod/layouts/`.

- Override `layouts/partials/home_info.html` to inject avatar image into the homepage intro.
- Custom CSS goes in `assets/css/extended/anyname.css` and is auto-bundled into the theme stylesheet.

Example `home_info.html` override: embed an `<img class="home-avatar">` before the `<h1>` and add `.home-avatar { border-radius: 50%; ... }` in `assets/css/extended/custom.css`.

## Creating Posts

### Method 1: Create manually in `content/posts/`

Posts live in `content/posts/<filename>.md`. Example frontmatter:

```yaml
---
title: "My First Post"
date: 2025-06-16
description: "Optional description"
tags: ["hugo", "papermod"]
author: "Me"
draft: false
showToc: false
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
# weight: 1  # pin post order
cover:
    image: "<image path or url>"
    alt: "alt text"
    caption: "caption text"
    relative: false
    hidden: true
---

Content goes here...
```

Use `<!--more-->` for the summary break on list pages.

### Method 2: Use archetype + `hugo new`

1. Create `archetypes/post.md` with a template (see wiki's Sample `Page.md`).
2. Run:

```bash
hugo new --kind post posts/my-first-post.md
```

## Creating Static Pages

Create pages outside `posts/` directly in `content/` (or in their own section).

Example frontmatter for a standalone page:

```yaml
---
title: "About"
date: 2025-06-16
showToc: false
draft: false
---
```

## Front Matter Variables (PaperMod)

- `showToc` / `TocOpen`: show/hide table of contents
- `hidemeta`: hide date, read-time, author
- `hideSummary`: hide summary in list views
- `ShowReadingTime`: show read time
- `ShowBreadCrumbs`: show breadcrumb nav
- `ShowPostNavLinks`: show prev/next post links
- `ShowWordCount`: show word count
- `disableShare`: hide share buttons
- `searchHidden`: hide from search
- `weight`: ordering / pin posts
- `cover.image`, `cover.alt`, `cover.caption`, `cover.relative`, `cover.hidden`
- ` canonicalURL`: canonical URL for cross-posts
- `aliases`: URL redirects

## Useful Commands

```bash
hugo server -D       # Start dev server with drafts
hugo server          # Start dev server without drafts
hugo new posts/<name>.md   # Create new content file
```

## Custom Head / Footer / Analytics

To inject custom HTML (analytics, CSP, extra `<head>` or footer content) without editing the theme:

- Create `layouts/partials/extend_head.html` — contents appended to `<head>`
- Create `layouts/partials/extend_footer.html` — contents appended to bottom of `<body>`

Current setup includes:
- Umami tracking script (`https://cloud.umami.is/script.js`)
- CSP meta tag (rendered only outside `hugo server` to avoid blocking livereload)

## CI / CD (GitHub Actions)

The site deploys to **GitHub Pages** via GitHub Actions.

- Workflow: `.github/workflows/deploy.yml`
- Trigger: push to `master` branch (or manual dispatch)
- Build steps: checkout with recursive submodules, install Hugo Extended, build with `hugo --minify`, upload `public/` artifact
- Deploy: uses `actions/deploy-pages@v4` (official GitHub Pages deploy action)

### Repository remote

```bash
git remote -v
# origin  git@github.com:MrSydar/mrsydar.github.io.git (fetch)
# origin  git@github.com:MrSydar/mrsydar.github.io.git (push)
```

### Required GitHub repo settings

1. Go to **Settings → Pages**
2. Under **Build and deployment**, set **Source** to **GitHub Actions**
3. First deploy may require you to approve the workflow run under **Actions → deploy**

## Constraints

- Use YAML format for config and frontmatter (repo convention).
- Do not edit files under `themes/PaperMod/` directly; override via `layouts/` or `assets/css/extended/` if needed.
- If adding CSS overrides, place them in `assets/css/extended/`.

_last updated: 2026-06-18T06:06:01Z by Hermes Agent_
