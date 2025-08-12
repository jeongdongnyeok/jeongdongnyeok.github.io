# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Jekyll-based personal blog hosted on GitHub Pages (`jeongdongnyeok.github.io`). The blog is written in Korean and focuses on AI, development, and daily life topics.

## Essential Commands

### Development
```bash
# Install dependencies
bundle install

# Run local development server (http://localhost:4000)
bundle exec jekyll serve

# Build the site for production
bundle exec jekyll build

# Clean build artifacts
bundle exec jekyll clean
```

## Architecture & Structure

### Core Components

1. **Theme**: Uses Minima 3.0.0.dev with auto skin (adaptive light/dark mode)
2. **Language**: Korean interface with Korean content
3. **Deployment**: GitHub Pages automatic deployment from master branch

### Key Files & Directories

- `_config.yml`: Main Jekyll configuration - controls site title, theme, plugins, and navigation
- `_posts/`: Blog posts in `YYYY-MM-DD-title.md` format
- `_layouts/`: Template hierarchy: base.html → home.html/post.html/page.html
- `_site/`: Generated static files (do not edit directly, excluded from git)
- `index.markdown`: Custom homepage showing 2 recent posts and category list

### Post Front Matter Structure

```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD HH:MM:SS +0900
categories: [category]
tags: [tag1, tag2]
---
```

Current categories: diary, Work
Current tags: 일상, 기록, 7월, ai, new, test, userstory

### Custom Features

1. **Homepage**: Shows 2 most recent posts + category navigation
2. **Category Archive**: `/categories.html` - Posts grouped by category
3. **Tag Archive**: `/tags.html` - Posts grouped by tags
4. **SEO**: Configured with jekyll-seo-tag plugin
5. **RSS Feed**: Auto-generated at `/feed.xml`

## Important Notes

- **Missing Files**: `portfolio.md` is referenced in header navigation but doesn't exist
- **Unconfigured Features**: Google Analytics and Disqus comments are included but not configured
- **Build Output**: `_site/` directory contains generated files - never edit these directly
- **Time Zone**: Posts use Korean time (+0900)
- **Theme Customization**: Minimal customization over default Minima theme