---
title: "React Server Components"
date: 2025-06-10
description: "First impressions after migrating a Next.js app to the App Router."
tags: ["react", "nextjs", "frontend"]
author: "Me"
draft: false
showToc: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---

I migrated a side project from Next.js Pages Router to the App Router. The biggest change was understanding where and how Server Components fit in.

<!--more-->

## What worked well

- Zero client JS for static content pages
- Streaming HTML feels instant
- Layouts are composable and persistent across navigation

## What confused me

- "use client" boundaries are easy to overuse
- Caching semantics changed significantly
- Error handling with error.tsx took some getting used to

More notes after I've shipped it to production.
