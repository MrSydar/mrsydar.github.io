---
title: "Neovim as My Daily Driver"
date: 2025-06-07
description: "How I switched from VS Code to Neovim and what I gained."
tags: ["neovim", "editor", "workflow"]
author: "Me"
draft: false
showToc: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---

After a decade in VS Code, I spent two weeks learning Neovim. It stuck.

<!--more-->

## Why I switched

- Editing speed: motions and text objects change how you think about code
- Startup time: instant, even on large repos
- Lua config: one language for everything, no JSON or YAML extensions needed

## What I miss

- Built-in debugger UI (though `nvim-dap` covers most cases)
- Effortless "search across workspace" (I'm fast with `ripgrep` now)

## Config philosophy

I started from `kickstart.nvim` and gradually replaced plugins with built-in features. The result is fast, stable, and completely mine.
