---
title: "Quartzsite"
description: "A public digital garden built with Quartz v4, demonstrating AI-native documentation patterns and content governance via code."
tags:
  - type/project
  - topic/quartz
  - topic/digital-gardens
  - topic/ai
  - topic/pkm
status: "active"
draft: false
publish: true
started: "2026-01-02"
repo: "https://github.com/aztres/quartzsite"
demo: "https://aztres.github.io/quartzsite/"
---

# Quartzsite

A public [[digital-gardens|digital garden]] built with Quartz v4, serving as both a second brain and a demonstration of [[ai-native-development|AI-native documentation patterns]]. The project showcases [[claude-skills-pattern|skills-based]] content management, [[documentation-as-architecture|architectural documentation]], and [[content-governance-via-code|automated quality governance]].

## Overview

**What it is:**
- Static site generator (Quartz v4) for publishing markdown notes
- Wiki-style linking between concepts
- Tag-based navigation and discovery
- Graph view of content relationships
- Automated deployment via GitHub Actions

**Why it exists:**
- Learn Quartz framework in practice
- Build public second brain for knowledge sharing
- Develop and test AI-assisted content workflows
- Demonstrate documentation-as-code patterns

## Status: Active

**Current State:**
- Site live at https://aztres.github.io/quartzsite/
- Content system operational (blog posts, evergreen notes, projects)
- [[content-manager-skill]] enforcing quality standards
- Deployment fully automated (git push → deployed in ~1 minute)

**Current Focus:**
- Creating evergreen notes for key concepts
- Writing blog posts about development journey
- Refining content taxonomy and linking strategy
- Building out pattern library

**Next Steps:**
- Add more evergreen notes on AI development patterns
- Create retrospectives for major work sessions
- Customize Quartz theme/components
- Integrate additional content types (weekly notes, learning logs)

## Key Features

### 1. AI-Native Documentation System

Three-layer documentation architecture for AI collaboration:

**Root Layer (`claude.md`):**
- Project overview and tech stack
- Build commands and deployment workflow
- Performance and context management guidelines
- Quick start guides for different work types

**Skills Layer (`.claude/skills/content-manager/`):**
- Frontmatter contracts and validation rules
- Tag taxonomy (type/*, topic/*, maturity/*, etc.)
- Linking strategy between content types
- Quality checklist before publishing

**Memory Layer (`.claude/retrospectives/`):**
- Session retrospectives capturing learnings
- Pattern documentation for reuse
- Decision logs and anti-patterns

### 2. Content Type System

Four first-class content types with distinct templates:

**Evergreen Notes** (`content/notes/`)
- Long-lived concept notes (Zettelkasten-style)
- Maturity tracking: sprout → sapling → tree
- Link to related concepts and projects

**Blog Posts** (`content/posts/YYYY-MM-DD-slug.md`)
- Time-stamped articles and learning logs
- Link to evergreen notes for depth
- Optional series support

**Projects** (`content/projects/`)
- Project documentation hubs
- Aggregate related notes and posts
- Status tracking: idea → active → paused → archived

**Profile** (`content/profile/`)
- Single canonical bio page
- Currently working on section
- Social links and contact

### 3. Content Governance

Automated enforcement of quality standards:

**Frontmatter Validation:**
```yaml
# Published only when BOTH are set
draft: false
publish: true

# Required fields per type
title: "Required string"
description: "1-2 sentences, <160 chars"
tags:
  - type/evergreen    # Exactly one
  - topic/something   # At least one
```

**Tag Taxonomy:**
- `type/*` - Content type (exactly one required)
- `topic/*` - Subject matter (≥1 required)
- `maturity/*` - Note development (Evergreens)
- `status/*` - Project state (Projects)
- `series/*` - Post series (Blog posts)

**Linking Strategy:**
- Blog posts → Link to evergreen notes
- Evergreen notes → Link to related concepts
- Projects → List related notes and posts

### 4. Automated Deployment

**Git Push = Deploy:**

```bash
git push origin v4
  ↓
GitHub Actions triggered
  ↓
Build with Quartz (Node.js 22)
  ↓
Deploy to GitHub Pages
  ↓
Live in ~1 minute
```

No manual deployment commands. No separate hosting dashboard.

**Self-Correcting Workflow:**
- AI reads GitHub Actions error logs
- Cross-references Quartz documentation
- Updates workflow configuration
- Retries deployment automatically

## Tech Stack

**Framework:**
- Quartz v4 (static site generator)
- Node.js 22+ (build requirement)
- TypeScript (configuration and plugins)

**Hosting:**
- GitHub Pages
- GitHub Actions for CI/CD
- Deployed from `v4` branch

**Content:**
- Markdown with YAML frontmatter
- Wiki-style links (`[[other-page]]`)
- Tag-based navigation
- Graph view of relationships

**AI Tooling:**
- Claude Code for development
- Content manager skill for quality enforcement
- Retrospective system for knowledge retention

## Development Workflow

### Content Creation

1. Invoke content-manager skill
2. Claude generates proper template
3. Fills required frontmatter
4. Adds wiki-links following strategy
5. Validates against quality checklist
6. Sets `publish: true` only when valid

### Deployment

1. Write/edit content locally
2. Test with `npx quartz build --serve`
3. Commit changes
4. Push to `v4` branch
5. GitHub Actions builds and deploys
6. Site updates automatically

### Quality Assurance

Pre-publish checklist enforced by [[content-manager-skill]]:
- Frontmatter complete and valid
- Tags follow taxonomy
- At least one outbound link
- Description under 160 characters
- No broken wiki-links

## Challenges & Learnings

### Discovery: Skills > Prompts

Initially explained frontmatter requirements every session. Now encoded as a skill—violations are impossible, not just discouraged.

### Discovery: Documentation as Build System

`.github/workflows/deploy.yml` isn't just automation—it's documentation that executes. When it fails, Claude reads the logs and fixes the config.

### Discovery: Error-Driven Iteration

Deployment assumed iteration, not one-shot success. Three failures → Node version fix → YAML syntax fix → success. AI handled all debugging.

### Discovery: Retrospectives Compound

Each session's learnings feed into next session. Patterns emerge, anti-patterns avoided, skills evolve.

## Related Notes

Concepts driving this project:

- [[claude-skills-pattern]] - AI assistance through structured constraints
- [[documentation-as-architecture]] - Docs as enforceable system design
- [[content-governance-via-code]] - Quality through automation
- [[retrospectives-for-knowledge-retention]] - Building institutional memory
- [[digital-gardens]] - Public learning and networked thought
- [[quartz-framework]] - Technical foundation

## Related Posts

Project development journey:

- [[2026-01-02-ai-native-documentation]] - How the system emerged
- *(More posts documenting the journey to come)*

## Links

- **Live Site**: [aztres.github.io/quartzsite](https://aztres.github.io/quartzsite/)
- **Repository**: [github.com/aztres/quartzsite](https://github.com/aztres/quartzsite)
- **Documentation**: [claude.md](https://github.com/aztres/quartzsite/blob/v4/claude.md)
- **Content Manager Skill**: [.claude/skills/content-manager/](https://github.com/aztres/quartzsite/tree/v4/.claude/skills/content-manager)

---

**Status updated: 2026-01-02**
**You're reading this on the site it describes.**
