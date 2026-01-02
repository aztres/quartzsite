# Quartzsite - Claude Code Guide

## Project Overview

**Quartzsite** is a digital garden built with Quartz v4, a fast static site generator for publishing Markdown-based notes and documentation. The site is deployed to GitHub Pages and features wiki-style linking, tags, search, and a graph view of content relationships.

**Main Components:**
- **Content** - Markdown files in `content/` folder
- **Quartz Configuration** - Site settings in `quartz.config.ts` and `quartz.layout.ts`
- **Components** - UI elements in `quartz/components/`
- **Plugins** - Content transformers and emitters in `quartz/plugins/`
- **Styles** - Custom CSS in `quartz/styles/`

**Deployment:**
- **Platform**: GitHub Pages
- **Repository**: https://github.com/aztres/quartzsite
- **Live Site**: https://aztres.github.io/quartzsite/
- **Branch**: `v4`
- **CI/CD**: GitHub Actions (`.github/workflows/deploy.yml`)

---

## Recent Updates (2026-01-02)

**Initial Content Setup:**
- ✅ **Folder Rename** - Renamed `contentlink/` to `content/` using `git mv`
  - Fixed Quartz content directory structure
  - Preserved git history
- ✅ **Homepage Created** - [content/index.md](content/index.md)
  - Fixed markdown formatting (removed escaped characters)
  - Added proper Quartz frontmatter
  - Welcome message and quick links
- ✅ **Sample Content Added**:
  - [content/about.md](content/about.md) - About the digital garden concept
  - [content/getting-started.md](content/getting-started.md) - Quartz usage guide
  - [content/example-note.md](content/example-note.md) - Example with wiki-links
- ✅ **Deployment** - Pushed to GitHub, site now shows content instead of RSS feed

**Files Modified:**
- [content/index.md](content/index.md) - Homepage with digital garden introduction
- [content/about.md](content/about.md) - Site information and tech stack
- [content/getting-started.md](content/getting-started.md) - How to use Quartz
- [content/example-note.md](content/example-note.md) - Sample note with links

---

## Tech Stack and Build

**Framework:**
- **Quartz v4** - Static site generator
- **TypeScript** - Configuration and plugins
- **Node.js 20+** - Runtime
- **npm** - Package manager

**Build Commands:**
```bash
# Development mode (local preview with hot reload)
npx quartz build --serve

# Production build (generates static site in public/)
npx quartz build

# Sync content from another location
npx quartz sync
```

**Local Development:**
- Run `npx quartz build --serve` to start local server
- Site available at http://localhost:8080
- Changes to content/ auto-rebuild
- Changes to config require restart

**Deployment Workflow:**
1. Edit content in `content/` folder
2. Test locally with `npx quartz build --serve`
3. Commit and push to `v4` branch
4. GitHub Actions builds and deploys automatically
5. Site updates at https://aztres.github.io/quartzsite/

---

## Folder Map

- **content/** — Markdown content files (notes, pages)
- **quartz/** — Quartz framework code
  - **quartz/components/** — UI components (Header, Footer, Graph, etc.)
  - **quartz/plugins/** — Transformers and emitters
  - **quartz/styles/** — CSS stylesheets
  - **quartz/util/** — Utility functions
- **public/** — Generated static site (git-ignored)
- **.github/workflows/** — GitHub Actions deployment config
- **quartz.config.ts** — Main Quartz configuration
- **quartz.layout.ts** — Layout and component configuration

---

## Coding Conventions

### Content Guidelines

**Frontmatter Format:**
```yaml
---
title: "Page Title"
tags:
  - tag1
  - tag2
date: 2026-01-02
---
```

**Wiki-style Links:**
- `[[other-page]]` - Links to other-page.md
- `[[other-page|Custom Text]]` - Link with custom text
- `[[folder/page]]` - Link to page in subfolder

**Content Organization:**
- Keep main pages in root of `content/`
- Create subfolders for categories: `content/notes/`, `content/projects/`
- Use tags for cross-cutting concerns
- Link liberally between related content

### Quartz Configuration

**Site Settings (quartz.config.ts):**
- Site title, description, author
- Base URL for deployment
- Plugin configuration
- Theme settings

**Layout Configuration (quartz.layout.ts):**
- Header, footer, sidebar components
- Component ordering and placement
- Page layout structure

**Custom Components:**
- Create in `quartz/components/` folder
- Export default component function
- Register in `quartz.layout.ts`

### File Naming

**Content Files:**
- Use lowercase with hyphens: `getting-started.md`
- Avoid spaces in filenames
- Use descriptive names

**Component Files:**
- PascalCase: `Header.tsx`, `Graph.tsx`
- Match component name to filename

---

## AI Usage Guidelines

### Working on This Project

**Respect Quartz Conventions:**
- Content goes in `content/` folder only
- Never edit files in `quartz/` unless customizing framework
- Configuration changes go in `quartz.config.ts` or `quartz.layout.ts`
- Custom styles go in `quartz/styles/custom.scss`

**Content Creation:**
- Always use proper Quartz frontmatter
- Create wiki-links to connect content
- Add tags for discoverability
- Test locally before pushing

**Using File References:**
- Use `@file` syntax: `@file content/index.md`
- Use `@folder` syntax: `@folder content/`
- Avoid pasting large code blocks when referencing

**Before Major Changes:**
- Commit current state
- Test locally with `npx quartz build --serve`
- Verify build succeeds before pushing
- Check GitHub Actions after pushing

**Common Pitfalls:**
- Don't edit `public/` folder (auto-generated)
- Don't commit `node_modules/`
- Don't break wiki-links when renaming files
- Ensure frontmatter YAML is valid

**Testing Changes:**
1. Make content/config changes
2. Run `npx quartz build --serve`
3. Preview at http://localhost:8080
4. Check for build errors in terminal
5. Test navigation and links
6. Commit and push to deploy

---

## Key Entry Points

**Main Configuration:**
- [quartz.config.ts](quartz.config.ts) - Site configuration
- [quartz.layout.ts](quartz.layout.ts) - Layout and components

**Content:**
- [content/index.md](content/index.md) - Homepage
- [content/](content/) - All site content

**Deployment:**
- [.github/workflows/deploy.yml](.github/workflows/deploy.yml) - GitHub Actions config

---

## Common Tasks

**Add a new page:**
1. Create `content/new-page.md`
2. Add frontmatter with title and tags
3. Write content with wiki-links
4. Link to it from other pages
5. Test locally, then push

**Add a new content category:**
1. Create folder: `content/category/`
2. Add pages in that folder
3. Link to category pages from index
4. Use consistent tags

**Customize site appearance:**
1. Edit `quartz/styles/custom.scss`
2. Or modify `quartz.layout.ts` for component changes
3. Test locally to verify changes
4. Push to deploy

**Update Quartz version:**
1. Check Quartz release notes
2. Update package.json version
3. Run `npm install`
4. Test thoroughly locally
5. Check for breaking changes
6. Deploy after testing

**Fix broken links:**
1. Use Quartz's link validation
2. Search for broken wiki-links
3. Update file paths or link targets
4. Re-test all affected pages

---

## Reference Documents Index

### Session & Task Management
- **[.claude/SESSION-SUMMARY.md](.claude/SESSION-SUMMARY.md)** - Running task list, completed work (to be created)

### Learning & Retrospectives
- **[.claude/RETROSPECTIVE-PROCESS.md](.claude/RETROSPECTIVE-PROCESS.md)** - How to create and use retrospectives
- **[.claude/retrospectives/](.claude/retrospectives/)** - Session retrospectives documenting learnings

### Implementation Guides
- To be added as the project evolves

---

## Notes for Claude

- Site deployed at: https://aztres.github.io/quartzsite/
- GitHub repo: https://github.com/aztres/quartzsite
- Main branch: `v4`
- Local preview: `npx quartz build --serve` → http://localhost:8080
- Package manifest: [package.json](package.json)
- Build output: `public/` (git-ignored)

**Quick References:**
- `npx quartz build --serve` - Local development server
- `npx quartz build` - Production build
- Content folder: [content/](content/)
- Config files: [quartz.config.ts](quartz.config.ts), [quartz.layout.ts](quartz.layout.ts)

**Project Context:**
- Digital garden for personal knowledge management
- Focus on wiki-style linking and discoverability
- Deployed automatically via GitHub Actions
- Content-first approach, minimal customization

---

*Created 2026-01-02 for Claude Code usage*
