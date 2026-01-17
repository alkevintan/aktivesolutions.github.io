# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll static site - a Ruby-based blog/website generator using the Minima theme.

## Development Commands

```bash
# Install dependencies
bundle install

# Start development server (auto-reloads on changes)
bundle exec jekyll serve

# Build the site for production
bundle exec jekyll build
```

**Important**: Changes to `_config.yml` require restarting the Jekyll server - the file is not auto-reloaded.

## Architecture

### Jekyll Structure

- **Pages**: Root-level markdown files (`index.markdown`, `about.markdown`) become site pages
- **Posts**: `_posts/` directory contains blog posts with naming format `YYYY-MM-DD-title.markdown`
- **Config**: `_config.yml` defines site-wide settings accessible via `{{ site.* }}` Liquid templates
- **Output**: `_site/` contains generated static files (gitignored)

### Front Matter

Jekyll uses YAML front matter at the top of files for configuration:

```yaml
---
layout: home
title: About
permalink: /about/
---
```

### Theme Customization

The site uses the **Minima** theme (`~> 2.5`). To override theme defaults, create files in your project:
- `_layouts/` - Override layout templates
- `_includes/` - Override partials
- `_sass/` - Override styles
- `assets/css/` - Custom CSS files

### Content Organization

- Pages use `layout: page` for standalone pages
- Homepage uses `layout: home`
- Blog posts are automatically styled with post layout
- The `jekyll-feed` plugin generates RSS/Atom feeds

### Key Dependencies

- **jekyll** (~> 4.4.1) - Static site generator
- **minima** (~> 2.5) - Default theme
- **jekyll-feed** (~> 0.12) - Feed generation plugin
- **webrick** (~> 1.9) - Ruby web server for development

## Common Patterns

### Creating a New Blog Post

Create a file in `_posts/` with the format `YYYY-MM-DD-title.markdown`:

```markdown
---
layout: post
title: "Post Title"
date: 2026-01-17 10:00:00 +0800
categories: example category
---

Your post content here...
```

### Creating a New Page

Create a `.markdown` file in the root directory:

```markdown
---
layout: page
title: Page Title
permalink: /page-slug/
---

Page content here...
```

### Liquid Template Variables

- `{{ site.title }}`, `{{ site.email }}`, etc. - Access config values
- `{{ page.title }}`, `{{ page.content }}` - Access current page values
- `{{ post.title }}`, `{{ post.url }}` - Access post data in loops
