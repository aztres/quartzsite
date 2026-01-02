# Content Manager Skill (Quartz Public Garden)

## Purpose

Provide **consistent** rules, templates, and workflows for managing public content in this Quartz-based digital garden:

- First-class public types: Evergreen notes, Blog posts, Projects, Profile.
- Enforce frontmatter contracts, tag schema, and linking patterns.
- Support draft/publish workflows and public-facing quality checks.

---

## Content Types

All public content lives under `content/` as Quartz expects. [ref: content-organization.md]

### Evergreen Notes

- **Purpose:** Long-lived public concepts and ideas (Zettelkasten-style).
- **Path pattern:** `content/notes/<slug>.md`
- **URL:** `/notes/<slug>/` (Quartz default routing)

### Blog Posts

- **Purpose:** Time-stamped essays and learning-in-public updates.
- **Path pattern:** `content/posts/YYYY-MM-DD-<slug>.md`
- **URL:** `/posts/YYYY-MM-DD-<slug>/`

### Projects

- **Purpose:** Public hubs for ongoing or completed projects.
- **Path pattern:** `content/projects/<slug>.md`
- **URL:** `/projects/<slug>/`

### Profile

- **Purpose:** Single canonical entry page with bio, social links, and "currently working on".
- **Path:** `content/profile/index.md`
- **URL:** `/profile/`

---

## Frontmatter Model

All first-class types must define both `draft` and `publish`. A page is **published** only if:

- `publish: true`
- `draft: false`

Any other combination → not published. [ref: frontmatter-standards.md]

### Evergreen Notes

Required fields:

```yaml
title: "Concept Title"
description: "Short 1–2 sentence summary for previews."
tags:
  - type/evergreen
  - topic/<something>
maturity: "sprout" # sprout | sapling | tree
draft: false
publish: true
```

### Blog Posts

Required fields:

```yaml
title: "Post Title"
description: "Short 1–2 sentence description for previews."
tags:
  - type/post
  - topic/<something>
date: 2026-01-02
draft: false
publish: true
```

### Projects

Required fields:

```yaml
title: "Project Name"
description: "What this project is and why it exists."
tags:
  - type/project
  - topic/<something>
status: "active" # idea | active | paused | archived
draft: false
publish: true
```

### Profile

Required fields:

```yaml
title: "Your Name"
description: "Short bio / what this site is."
tags:
  - type/profile
layout: "profile"
draft: false
publish: true
```

---

## Tagging Schema

Quartz auto-generates tag listing pages; tags must be structured for useful navigation.

### Namespaces

- **Type tags** (exactly one per page):
  - `type/evergreen`
  - `type/post`
  - `type/project`
  - `type/profile`

- **Topic tags** (1+ per page):
  - `topic/<domain>` e.g. `topic/rust`, `topic/ai`, `topic/pkm`, `topic/quartz`.

- **Optional:**
  - `maturity/sprout | maturity/sapling | maturity/tree` (for Evergreens)
  - `status/<state>` mirroring `status` if desired
  - `series/<name>` for future series (e.g. weekly notes)

### Per-Type Requirements

- **Evergreen:**
  - Required: `type/evergreen`, ≥1 `topic/*`
  - Optional: `maturity/*`

- **Blog post:**
  - Required: `type/post`, ≥1 `topic/*`
  - Optional: `series/*`

- **Project:**
  - Required: `type/project`, ≥1 `topic/*`
  - Optional: `status/*`

- **Profile:**
  - Required: `type/profile`

[ref: tagging-taxonomy.md]

---

## Linking Strategy (Public Garden)

Default linking behavior follows public second brain / digital garden patterns. [ref: linking-strategy.md]

### Blog Posts

When creating or updating a Blog post:

- Always link to at least one relevant Evergreen note if one exists.
- When about a specific project, link to that Project page in intro or outro.
- Add a `## Related` section at the end with:
  - 1–3 Evergreen notes.
  - 0–2 Project links when relevant.

### Evergreen Notes

When creating or updating an Evergreen note:

- Prefer linking to other Evergreen notes for core concepts.
- When a concept is central to one or more Projects, add a "Projects" or "Used in" list with links to those Project pages.

### Projects

When creating or updating a Project page:

- Include sections:
  - `## Related notes` (Evergreen)
  - `## Related posts` (Blog; can be empty but present).
- When summarizing a project, aggregate from:
  - The Project page itself.
  - Linked Evergreens and Posts.

### Profile

When updating the Profile:

- Include:
  - "Find me on" social links.
  - A "Currently working on" section linking to 2–5 `status: active` Projects.
  - A link to a Posts index or "Latest posts" list if available.

---

## Lifecycle Patterns

### New Content Creation

Given a request like "Create a new <type> about X":

1. Determine type: Evergreen | Blog post | Project | Profile.
2. Generate slug: kebab-case of title.
3. Choose path:
   - Evergreen → `content/notes/<slug>.md`
   - Blog → `content/posts/YYYY-MM-DD-<slug>.md`
   - Project → `content/projects/<slug>.md`
   - Profile → `content/profile/index.md` (single instance)
4. Insert template for that type. [ref: content-templates.md]
5. Fill required frontmatter fields.
6. Populate an outline with required sections.
7. Add initial wiki-links according to linking strategy.

### Updating Content

When updating any first-class content:

- Do not change path unless explicitly requested.
- Preserve and extend existing frontmatter.
- Maintain tag and link consistency (do not silently drop tags/links).
- For major changes, prefer additive edits over full rewrites unless asked.

### Archival / Unpublishing

- To unpublish without deleting:
  - Set `publish: false` or `draft: true`.
- For Projects:
  - Prefer updating `status: archived` and optionally note this in the body.
- Avoid deleting files that have inbound links; instead:
  - Mark as archived and add a short explanation at the top.

---

## Quality Standards

Before considering a page "publishable" (`publish: true`, `draft: false`), check:

- **Frontmatter:**
  - All required fields present for type.
  - At least one `topic/*` tag (except Profile).
- **Body:**
  - Clear summary at top (thesis or overview).
  - Logical headings (`##`) for sections.
  - At least one outbound wiki-link for Evergreen/Blog/Project when appropriate.
- **Consistency:**
  - Type tags and topic tags follow schema.
  - Links to other first-class types follow linking rules.

[ref: quality-checklist.md]

---

## AI Usage Guidelines (Claude)

When acting as Content Manager:

### Always:
- Use correct template and path for the requested type.
- Enforce frontmatter and tag requirements.
- Respect draft/publish semantics.

### Should:
- Suggest reorganization or refactors explicitly.
- Propose linking targets and tag improvements instead of applying risky changes silently.

### Must Not:
- Remove user-authored sections without explicit instruction.
- Change file paths without updating references and explaining impact.

---

## Reference Documentation

- [frontmatter-standards.md](reference/frontmatter-standards.md) - Frontmatter field definitions and examples
- [content-organization.md](reference/content-organization.md) - Folder structure and path mapping
- [linking-strategy.md](reference/linking-strategy.md) - Interlinking patterns and examples
- [tagging-taxonomy.md](reference/tagging-taxonomy.md) - Tag namespace definitions
- [content-templates.md](reference/content-templates.md) - Markdown templates per type
- [quality-checklist.md](reference/quality-checklist.md) - Pre-publish validation checklist

---

*Inspired by public second brain patterns from ssp.sh/brain*
