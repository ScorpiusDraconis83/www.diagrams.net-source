# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is the Jekyll source for **www.drawio.com**, the marketing/documentation site for draw.io (diagrams.net). It is an internal site not open to external PRs.

## Build Commands

```bash
# Install dependencies
bundle install

# Run local development server (serves at http://localhost:4000)
bundle exec jekyll serve

# Build static site (outputs to _site/)
bundle exec jekyll build
```

## Architecture

### Content Types

**Blog Posts** (`_posts/`): ~283 markdown files with date-prefixed filenames (`YYYY-MM-DD-slug.md`). Front matter requires: `layout: post`, `author`, `slug`, `title`, `tags`, `categories`.

**FAQ Collection** (`doc/faq/`): ~270 markdown files. Front matter requires: `layout: page`, `faq: true`, `title`, `categories` (from the 23 predefined FAQ categories in `_config.yml`).

**Documentation** (`doc/`): Getting started guides and integration docs using `layout: page`.

**Static Pages** (`pages/`): Main site pages (about, features, integrations) using `layout: page`.

**Blog Category Pages** (`blog/`): HTML files that generate category archive pages using `layout: category`.

### Layout Hierarchy

```
_layouts/
├── default.html    → Base: header + content + footer
├── page.html       → Static pages (includes pages/single-page.html)
├── post.html       → Blog posts (includes blog/single-article.html)
├── blog.html       → Blog index (includes blog/index.html)
├── category.html   → Category archives (includes blog/category.html)
└── doc.html        → Documentation (same as page.html)
```

All layouts include `header.html` and `footer.html` from `_includes/`.

### Key Configuration

`_config.yml` defines:
- `permalink: /blog/:slug` - Blog post URL structure
- `collections: [faq]` - FAQ collection
- `faq-categories` - 23 predefined categories for FAQ/blog content

### Assets

- `/assets/css/theme.css` - Main stylesheet (large, custom styles)
- `/assets/js/search.js` - Client-side search functionality
- `/assets/img/blog/` - Blog post images (organized in subdirectories)
- `/assets/svg/icons/` - Icon SVGs

### Front Matter Patterns

Blog post:
```yaml
---
layout: post
author: draw.io
slug: your-post-slug
title: Post Title
tags: [tag1, tag2]
categories: [category1, category2]
---
```

FAQ item:
```yaml
---
title: FAQ Title
layout: page
faq: true
categories: [Category1, Category2]
---
```
