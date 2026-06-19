# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Architecture

This is a Hugo static site generator project for Andrea Grandi's personal blog (andreagrandi.it). The site uses the hugo-theme-stack/v3 theme.

### Key Directory Structure
- `content/posts/` - Blog posts organized by year (2007-2025) 
- `config/_default/` - Hugo configuration files (YAML format)
- `layouts/` - Custom theme templates and partials
- `static/` - Static assets (images, files, etc.)
- `public/` - Generated site output (not committed to git)
- `resources/_gen/` - Hugo-generated resources cache

### Content Organization
- Posts are organized by year in `content/posts/YYYY/`
- Each post has its own directory with `index.md` and associated images
- Site uses Hugo's page bundles for content organization
- Main sections: posts, about, cv, archives, search

## Development Commands

### Core Hugo Commands
```bash
# Start development server
hugo server

# Start development server with drafts
hugo server -D

# Build the site
hugo build

# Build for production (minified)
hugo --minify

# Check site configuration
hugo config

# Create new post
hugo new posts/YYYY/post-title/index.md
```

### Site Management
```bash
# Clean generated resources
rm -rf resources/_gen/

# Clean public directory  
rm -rf public/

# Update theme (Go module)
hugo mod get -u
hugo mod tidy
```

## Configuration Details

The site uses YAML configuration files in `config/_default/`:
- `config.yaml` - Main site configuration
- `params.yaml` - Theme-specific parameters and customization
- `menu.yaml` - Navigation menus (main and social)
- `module.yaml` - Hugo module configuration for theme
- `markup.yaml` - Markdown rendering configuration

The theme is loaded as a Hugo module via `github.com/CaiJimmy/hugo-theme-stack/v3`.

## Content Guidelines

- All posts should be in `content/posts/YYYY/` directories
- Use Hugo's page bundle format with `index.md` and local images
- Front matter should include appropriate categories and tags
- Images should be co-located with posts in the same directory

## New posts

- When I ask you to create a new post with title "This is my new blog post":
    - Compose a <slug> from the title of the post
    - if we are on the `master` branch you must create a new branch (based on the <slug>)
    - you must create one in the following folder: content/posts/<year>/<number>-<slug>
    - the <year> must be the current year
    - the <number> must be the next number after the last folder prefix (ie: if 6-my-blog-post exists, next <number> is 7)
    - inside the created folder add an `index.md` with the structure of other existing posts
