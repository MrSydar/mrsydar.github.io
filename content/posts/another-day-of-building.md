---
title: "Another Day of Building"
date: 2025-06-14
description: "Short post about experimenting with static site generators."
tags: ["hugo", "workflow"]
author: "Me"
draft: false
showToc: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---

Today I spent some time setting up a Hugo site with the PaperMod theme. The process is straightforward once you understand the content structure and frontmatter variables.

<!--more-->

## What I learned

- `content/posts/` is the default section for blog posts
- `hugo.yaml` controls site-wide settings, menus, and theme params
- The `homeInfoParams` block replaces the default "profile mode" with a nice intro section
- Search works via Fuse.js and needs a `search.md` page with `layout: search`

More posts coming soon.
