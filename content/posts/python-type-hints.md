---
title: "Python Type Hints"
date: 2025-06-08
description: "Why I started adding type hints to all my Python scripts."
tags: ["python", "typing", "developer-experience"]
author: "Me"
draft: false
showToc: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---

I used to think Python type hints were just noise. After refactoring a large script with `mypy`, I changed my mind.

<!--more-->

## The turning point

A runtime bug caused by passing a string where an int was expected burned half a day. With type hints and `mypy --strict`, it would have been caught in seconds.

## What I do now

- Type hint every public function
- Run `mypy` in CI next to tests
- Use `dataclasses` and `TypedDict` for structured data

It's not perfect, but it's way better than guesswork.
