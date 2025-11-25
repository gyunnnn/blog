# CLAUDE.md - AI Assistant Guide for JEGYUN's Blog

This document provides comprehensive guidance for AI assistants working with this Hexo blog repository.

## Repository Overview

**Project Type**: Personal Blog
**Framework**: Hexo (v8.1.1)
**Theme**: Cactus (forked)
**Language**: Korean (ko-KR)
**Author**: PARK JEGYUN
**Site URL**: https://gyunnnn.github.io
**Deployment**: GitHub Pages (gyunnnn/gyunnnn.github.io)

## Project Structure

```
blog/
├── _config.yml              # Main Hexo configuration
├── _config.landscape.yml    # Alternative theme config (not in use)
├── package.json            # Node.js dependencies
├── scaffolds/              # Templates for new content
│   ├── draft.md           # Draft template
│   ├── page.md            # Page template
│   └── post.md            # Post template
├── source/                # Blog content source
│   ├── _posts/            # Published blog posts
│   ├── _drafts/           # Draft posts
│   ├── categories/        # Categories index page
│   └── tags/              # Tags index page
└── themes/                # Theme files
    └── cactus/            # Cactus theme (forked)
        ├── _config.yml    # Theme-specific configuration
        ├── languages/     # i18n translations
        ├── layout/        # Template files
        ├── scripts/       # Theme scripts
        └── source/        # Theme assets (CSS, JS, images)
```

### Key Directories

- **blog/source/_posts/**: All published blog posts (Markdown files)
- **blog/source/_drafts/**: Work-in-progress posts not yet published
- **blog/themes/cactus/**: Custom theme files (forked from probberechts/hexo-theme-cactus)
- **blog/public/**: Generated static site (gitignored, created on build)

## Technology Stack

### Core Dependencies
- **Hexo**: Static site generator (v8.1.1)
- **Node.js**: Runtime environment
- **Markdown**: Content format
- **EJS**: Template engine
- **Stylus**: CSS preprocessor

### Hexo Plugins
- `hexo-deployer-git`: Deploy to GitHub Pages
- `hexo-generator-archive`: Generate archive pages
- `hexo-generator-category`: Generate category pages
- `hexo-generator-index`: Generate index pages
- `hexo-generator-tag`: Generate tag pages
- `hexo-renderer-ejs`: EJS template renderer
- `hexo-renderer-marked`: Markdown renderer
- `hexo-renderer-stylus`: Stylus CSS renderer
- `hexo-server`: Local development server

## Configuration Files

### Main Configuration: `blog/_config.yml`

Key settings:
- **Site Info**: Title, author, language (Korean), timezone (Asia/Seoul)
- **URL**: https://gyunnnn.github.io
- **Permalink**: `:year/:month/:day/:title/`
- **Theme**: `cactus`
- **Deployment**: Git deployment to gyunnnn.github.io (main branch)
- **Posts per page**: 10
- **Drafts**: Enabled (`render_drafts: true`)
- **Post asset folders**: Enabled (`post_asset_folder: true`)

### Theme Configuration: `blog/themes/cactus/_config.yml`

Key customizations:
- **Color scheme**: `dark`
- **Language**: Korean (ko)
- **Navigation**: Home, Articles, Category, Tag
- **Social links**: GitHub (gyunnnn), Email (parkjekyun@gmail.com)
- **Comments**: Giscus enabled (gyunnnn/gyunnnn.github.io)
- **CDN**: Enabled for external resources
- **Features**:
  - Tags overview enabled
  - Post count: 5 most recent on homepage
  - Show all posts: true
  - Updated date display: enabled

## Development Workflows

### Setting Up Local Environment

```bash
# Navigate to blog directory
cd blog

# Install dependencies
npm install

# Start local server (default: http://localhost:4000)
npm run server
# or
hexo server
```

### Creating New Content

#### New Blog Post
```bash
cd blog
hexo new post "Post Title"
# Creates: source/_posts/Post-Title.md
```

#### New Draft
```bash
cd blog
hexo new draft "Draft Title"
# Creates: source/_drafts/Draft-Title.md
```

#### New Page
```bash
cd blog
hexo new page "page-name"
# Creates: source/page-name/index.md
```

### Post Front Matter Template

```yaml
---
title: Post Title
date: YYYY-MM-DD HH:mm:ss
tags:
  - tag1
  - tag2
categories:
  - Category Name
---
```

### Building and Deploying

```bash
# Clean generated files
npm run clean
# or
hexo clean

# Generate static files (outputs to public/)
npm run build
# or
hexo generate

# Deploy to GitHub Pages
npm run deploy
# or
hexo deploy
```

## Git Workflow

### Current Branch Structure
- Development happens on feature branches starting with `claude/`
- Branch format: `claude/claude-md-midsw0ubxema5fi2-<session-id>`
- Never push directly to main branch

### Deployment Repository
- Source code: gyunnnn/blog
- Deployment target: gyunnnn/gyunnnn.github.io (main branch)
- Deployment is automated via `hexo deploy` command

### Important Git Conventions
- Commits should be descriptive and concise
- Use Korean or English for commit messages (preference: Korean based on recent commits)
- Follow the existing commit message style
- Always test builds locally before pushing

## Content Guidelines

### Blog Post Conventions

1. **File naming**: Posts are named with title in the filename
2. **Language**: Primary language is Korean (ko-KR)
3. **Asset management**: Each post can have its own folder for images/assets (enabled)
4. **Draft workflow**: Use drafts for work in progress
5. **Tags and Categories**: Use meaningful tags and categories for organization

### Markdown Features

Hexo uses `hexo-renderer-marked` with the following features:
- Standard Markdown syntax
- Code highlighting (highlight.js)
- Line numbers enabled for code blocks
- Post asset folder support for images

## Important Files to Never Modify

1. **blog/node_modules/**: Dependencies (gitignored)
2. **blog/public/**: Generated output (gitignored)
3. **blog/db.json**: Hexo database (gitignored)
4. **blog/.deploy_git/**: Deployment cache (gitignored)
5. **blog/package-lock.json**: Unless updating dependencies

## Files Safe to Modify

1. **blog/source/_posts/*.md**: Blog posts
2. **blog/source/_drafts/*.md**: Draft posts
3. **blog/_config.yml**: Main configuration (with caution)
4. **blog/themes/cactus/_config.yml**: Theme configuration
5. **blog/scaffolds/*.md**: Templates for new content

## Common AI Assistant Tasks

### Task 1: Create a New Blog Post

```bash
cd blog
hexo new post "Title of the Post"
```

Then edit `blog/source/_posts/Title-of-the-Post.md` with content.

### Task 2: Update Existing Post

1. Read the post: `blog/source/_posts/<post-name>.md`
2. Make edits using the Edit tool
3. Test locally: `cd blog && hexo server`
4. Commit and push changes

### Task 3: Modify Theme Settings

1. Read `blog/themes/cactus/_config.yml`
2. Make careful edits (avoid breaking syntax)
3. Test changes with local server
4. Commit changes

### Task 4: Add New Navigation Item

Edit `blog/themes/cactus/_config.yml`:
```yaml
nav:
  home: /
  articles: /archives/
  category: /categories/
  tag: /tags/
  new_page: /new-page/  # Add this
```

Create the page:
```bash
cd blog
hexo new page "new-page"
```

### Task 5: Full Build and Deploy

```bash
cd blog
hexo clean
hexo generate
hexo deploy
```

### Task 6: Search for Content

Use Grep to search within posts:
```bash
# Search in all posts
grep -r "search term" blog/source/_posts/

# Search in specific files
grep "search term" blog/source/_posts/*.md
```

## Debugging Common Issues

### Issue 1: Server Won't Start
- Check if port 4000 is in use
- Ensure dependencies are installed: `npm install`
- Check for syntax errors in `_config.yml`

### Issue 2: Build Fails
- Run `hexo clean` first
- Check for YAML syntax errors in front matter
- Verify all dependencies are installed

### Issue 3: Deployment Fails
- Verify deployment configuration in `_config.yml`
- Check git credentials
- Ensure `hexo-deployer-git` is installed

### Issue 4: Theme Not Applying
- Verify theme name in `_config.yml` matches folder name
- Check theme configuration syntax
- Run `hexo clean` and rebuild

## NPM Scripts Reference

| Command | Description |
|---------|-------------|
| `npm run build` | Generate static files |
| `npm run clean` | Clean generated files |
| `npm run deploy` | Deploy to GitHub Pages |
| `npm run server` | Start local development server |

## Hexo CLI Commands

| Command | Description |
|---------|-------------|
| `hexo init` | Initialize a new Hexo site |
| `hexo new [layout] <title>` | Create new post/page/draft |
| `hexo generate` | Generate static files |
| `hexo server` | Start local server |
| `hexo deploy` | Deploy to remote |
| `hexo clean` | Clean cache and generated files |
| `hexo list <type>` | List all routes/posts/pages/etc |
| `hexo version` | Display version info |

## Best Practices for AI Assistants

### DO:
1. ✅ Always read files before editing them
2. ✅ Use the Edit tool for existing files
3. ✅ Test builds locally when making configuration changes
4. ✅ Preserve YAML formatting and indentation
5. ✅ Respect the Korean language preference
6. ✅ Use descriptive commit messages
7. ✅ Check git status before committing
8. ✅ Follow the existing code and content style

### DON'T:
1. ❌ Don't create new files when editing existing ones
2. ❌ Don't modify generated files (public/, db.json)
3. ❌ Don't change deployment configuration without confirmation
4. ❌ Don't add unnecessary dependencies
5. ❌ Don't break YAML syntax in configuration files
6. ❌ Don't commit node_modules or generated files
7. ❌ Don't push directly to main branch
8. ❌ Don't remove existing content without explicit instruction

## Security Considerations

1. **No sensitive data**: Don't commit API keys, tokens, or credentials
2. **Public repository**: Assume all code is publicly visible
3. **Deployment keys**: GitHub deployment uses git protocol (configured)
4. **CDN resources**: External resources loaded from cdnjs.com

## Maintenance Tasks

### Regular Maintenance
- Update dependencies periodically: `npm update`
- Check for Hexo updates: `npm outdated`
- Review and clean up old drafts
- Test all functionality after updates

### Content Maintenance
- Review and update outdated posts
- Fix broken links
- Optimize images in post asset folders
- Clean up unused tags and categories

## Resources and Documentation

- **Hexo Docs**: https://hexo.io/docs/
- **Hexo Commands**: https://hexo.io/docs/commands
- **Cactus Theme**: https://github.com/probberechts/hexo-theme-cactus
- **Hexo Writing**: https://hexo.io/docs/writing.html
- **Hexo Deployment**: https://hexo.io/docs/one-command-deployment.html

## Quick Reference

### File Locations
- Blog posts: `blog/source/_posts/`
- Drafts: `blog/source/_drafts/`
- Main config: `blog/_config.yml`
- Theme config: `blog/themes/cactus/_config.yml`
- Templates: `blog/scaffolds/`

### Important URLs
- Production site: https://gyunnnn.github.io
- GitHub repo: gyunnnn/blog
- Deployment target: gyunnnn/gyunnnn.github.io

### Contact
- Author: PARK JEGYUN
- Email: parkjekyun@gmail.com
- GitHub: github.com/gyunnnn

---

**Last Updated**: 2025-11-24
**Hexo Version**: 8.1.1
**Theme**: Cactus (forked)
