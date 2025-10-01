---
links: []
title: React Notes page
description: Notes on react 19
seo:
  title: React Notes page
  description: Notes on react 19
---

## Rendering optimization via actions
- works with server-side logic, client side feedback
- Automatic Pending State Management (reduce the boilerplate code and additional rerenders that might appear with it)
- **optimistic updates:** rendering starts in the same time as the request with an optimistic value, if the request fails it fallsback to the initial State
- 