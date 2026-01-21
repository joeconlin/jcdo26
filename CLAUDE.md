# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site using the [Stack theme](https://github.com/CaiJimmy/hugo-theme-stack) via Hugo modules. The site is "Joe's Fieldnotes" and deploys to GitHub Pages.

## Common Commands

```bash
# Run local development server (includes draft posts)
hugo server -D

# Build for production
hugo --minify --gc

# Update theme to latest version
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v3
hugo mod tidy
```

The dev server runs on port 1313 by default.

## Architecture

**Configuration:** Split TOML files in `config/_default/`:
- `config.toml` - Base URL, language, pagination, Git info
- `params.toml` - Theme parameters (sidebar, widgets, comments, etc.)
- `menu.toml` - Navigation and social links
- `module.toml` - Hugo module imports (theme)

**Content Structure:**
- `content/post/` - Blog posts (main section per `mainSections` param)
- `content/page/` - Static pages (archives, search, links)
- `content/categories/` - Category metadata

Posts use Hugo page bundles (folder with `index.md` + assets).

**Deployment:** GitHub Actions workflow (`.github/workflows/deploy.yml`) builds and deploys to `gh-pages` branch on push to `master`.

## Theme Customization

The Stack theme is loaded as a Hugo module. To override theme templates or assets, create matching files in your local `layouts/` or `assets/` directories.
