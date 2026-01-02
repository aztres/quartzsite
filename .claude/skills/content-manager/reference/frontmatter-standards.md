# Frontmatter Standards

Defines required and optional fields per content type, field semantics, and validation rules.

---

## Publishing Semantics

### Draft and Publish Fields

Every first-class content type MUST have both fields:

```yaml
draft: false
publish: true
```

**Publishing Logic:**

| `draft` | `publish` | Result |
|---------|-----------|--------|
| `false` | `true`    | ✅ Published and visible |
| `true`  | `true`    | ❌ Not published (draft) |
| `false` | `false`   | ❌ Not published (unpublished) |
| `true`  | `false`   | ❌ Not published (draft + unpublished) |

**Only** `draft: false` AND `publish: true` means the content is live.

---

## Evergreen Notes

### Required Fields

```yaml
title: "Concept Title"
description: "Short 1–2 sentence summary for previews."
tags:
  - type/evergreen
  - topic/<something>
maturity: "sprout"
draft: false
publish: true
```

### Field Definitions

- **`title`** (string, required)
  - The concept name
  - Should be clear and specific
  - Use title case

- **`description`** (string, required)
  - 1-2 sentences explaining the concept
  - Used in preview cards and SEO
  - Keep under 160 characters for SEO

- **`tags`** (array, required)
  - MUST include exactly one `type/evergreen`
  - MUST include at least one `topic/*` tag
  - MAY include `maturity/*` tag
  - See [tagging-taxonomy.md](tagging-taxonomy.md)

- **`maturity`** (string, required)
  - Values: `sprout` | `sapling` | `tree`
  - Indicates how developed the note is:
    - **sprout**: Early thoughts, rough notes
    - **sapling**: Developing ideas, needs work
    - **tree**: Well-developed, stable concept
  - Update as note evolves

- **`draft`** (boolean, required)
  - `true` = work in progress
  - `false` = ready for public

- **`publish`** (boolean, required)
  - `true` = visible when not draft
  - `false` = hidden even if not draft

### Optional Fields

```yaml
created: "2026-01-02"
updated: "2026-01-02"
aliases: ["Alternative Name", "Synonym"]
```

---

## Blog Posts

### Required Fields

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

### Field Definitions

- **`title`** (string, required)
  - The post title
  - Should be engaging and descriptive
  - Use title case or sentence case consistently

- **`description`** (string, required)
  - 1-2 sentences summarizing the post
  - Used in preview cards and SEO
  - Should entice readers

- **`tags`** (array, required)
  - MUST include exactly one `type/post`
  - MUST include at least one `topic/*` tag
  - MAY include `series/*` tag for post series

- **`date`** (date, required)
  - Format: `YYYY-MM-DD`
  - Publication date
  - MUST match filename date for posts

- **`draft`** (boolean, required)
- **`publish`** (boolean, required)

### Optional Fields

```yaml
series: "series-name"
updated: "2026-01-03"
author: "Your Name"
```

---

## Projects

### Required Fields

```yaml
title: "Project Name"
description: "What this project is and why it exists."
tags:
  - type/project
  - topic/<something>
status: "active"
draft: false
publish: true
```

### Field Definitions

- **`title`** (string, required)
  - Project name
  - Clear and memorable

- **`description`** (string, required)
  - What the project is and why
  - Elevator pitch length
  - Used in preview cards

- **`tags`** (array, required)
  - MUST include exactly one `type/project`
  - MUST include at least one `topic/*` tag
  - MAY include `status/*` tag mirroring status field

- **`status`** (string, required)
  - Values: `idea` | `active` | `paused` | `archived`
  - Current project state:
    - **idea**: Conceptual, not started
    - **active**: Currently working on it
    - **paused**: On hold temporarily
    - **archived**: Completed or discontinued

- **`draft`** (boolean, required)
- **`publish`** (boolean, required)

### Optional Fields

```yaml
started: "2025-12-01"
completed: "2026-06-01"
repo: "https://github.com/user/project"
demo: "https://project.example.com"
```

---

## Profile

### Required Fields

```yaml
title: "Your Name"
description: "Short bio / what this site is."
tags:
  - type/profile
layout: "profile"
draft: false
publish: true
```

### Field Definitions

- **`title`** (string, required)
  - Your name or site name

- **`description`** (string, required)
  - Brief bio or site tagline
  - First impression for visitors

- **`tags`** (array, required)
  - MUST include `type/profile`
  - No topic tags required for profile

- **`layout`** (string, required)
  - Value: `profile`
  - Enables profile-specific layout (if configured in Quartz)

- **`draft`** (boolean, required)
- **`publish`** (boolean, required)

### Optional Fields

```yaml
social:
  github: "username"
  twitter: "handle"
  email: "your@email.com"
```

---

## Validation Rules

### Required Field Validation

Before saving any content, verify:

1. All required fields are present
2. Field values match expected types (string, boolean, array, date)
3. Tags include required `type/*` tag
4. Date fields use `YYYY-MM-DD` format
5. Status/maturity use valid enum values

### Tag Validation

1. Exactly ONE `type/*` tag per page
2. At least ONE `topic/*` tag (except Profile)
3. Tag format: `namespace/value` (lowercase, kebab-case)
4. No spaces in tags

### Publishing Validation

Before setting `publish: true` and `draft: false`:

1. All required fields present and valid
2. Description is meaningful (not placeholder)
3. Body content exists (not empty template)
4. At least one outbound link (for Evergreen/Blog/Project)
5. Quality checklist passed

---

## Examples

### Valid Evergreen Note Frontmatter

```yaml
---
title: "Zettelkasten Method"
description: "A personal knowledge management system using interconnected atomic notes."
tags:
  - type/evergreen
  - topic/pkm
  - topic/note-taking
  - maturity/tree
maturity: "tree"
draft: false
publish: true
created: "2025-11-15"
updated: "2026-01-02"
---
```

### Valid Blog Post Frontmatter

```yaml
---
title: "Building a Public Second Brain with Quartz"
description: "How I set up a digital garden using Quartz v4 and GitHub Pages."
tags:
  - type/post
  - topic/quartz
  - topic/pkm
  - series/digital-garden
date: 2026-01-02
series: "digital-garden"
draft: false
publish: true
---
```

### Valid Project Frontmatter

```yaml
---
title: "Quartzsite"
description: "A public digital garden and second brain built with Quartz."
tags:
  - type/project
  - topic/quartz
  - topic/pkm
  - status/active
status: "active"
draft: false
publish: true
started: "2026-01-02"
repo: "https://github.com/aztres/quartzsite"
demo: "https://aztres.github.io/quartzsite/"
---
```

---

## Common Mistakes

### ❌ Missing Required Fields

```yaml
---
title: "My Note"
tags:
  - topic/something
# MISSING: description, type tag, maturity, draft, publish
---
```

### ❌ Wrong Publishing Combo

```yaml
---
draft: true
publish: true
# This is DRAFT, not published!
---
```

### ❌ Multiple Type Tags

```yaml
---
tags:
  - type/evergreen
  - type/post  # ERROR: Only ONE type tag allowed!
---
```

### ❌ No Topic Tags

```yaml
---
tags:
  - type/evergreen
  # ERROR: Need at least one topic/* tag
---
```

---

*Frontmatter is the contract between your content and Quartz. Get it right and everything else follows.*
