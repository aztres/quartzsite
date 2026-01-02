# Tagging Taxonomy

Formal definition of tag namespaces, values, and usage rules for Quartz digital garden content.

---

## Tag Philosophy

**Tags serve three purposes:**

1. **Classification** - What type of content is this?
2. **Categorization** - What topics does it cover?
3. **Status** - What state is it in?

**Tags enable:**
- Automatic tag pages in Quartz
- Content filtering and discovery
- Reader navigation by topic

---

## Tag Format

### Structure

```
namespace/value
```

**Rules:**
- Lowercase only
- Kebab-case for multi-word values
- Forward slash separator
- No spaces
- Descriptive values

**Examples:**
- ✅ `type/evergreen`
- ✅ `topic/rust-programming`
- ✅ `maturity/tree`
- ❌ `Type/Evergreen` (wrong case)
- ❌ `topic/rust programming` (space)
- ❌ `rust` (no namespace)

---

## Required Tag Namespaces

### Type Namespace (`type/*`)

**Purpose:** Content type classification

**Rules:**
- Exactly **ONE** `type/*` tag per page
- Required for ALL content

**Values:**

| Tag | Content Type | Description |
|-----|--------------|-------------|
| `type/evergreen` | Evergreen Note | Long-lived concept notes |
| `type/post` | Blog Post | Time-stamped articles |
| `type/project` | Project Page | Project documentation |
| `type/profile` | Profile Page | Personal profile |

**Examples:**
```yaml
tags:
  - type/evergreen
  - topic/pkm
```

---

### Topic Namespace (`topic/*`)

**Purpose:** Subject matter categorization

**Rules:**
- **At least ONE** `topic/*` tag per page (except Profile)
- Multiple topic tags allowed and encouraged
- Use specific, descriptive values

**Common Topics:**

| Topic | Usage |
|-------|-------|
| `topic/rust` | Rust programming language |
| `topic/quartz` | Quartz framework |
| `topic/pkm` | Personal knowledge management |
| `topic/ai` | Artificial intelligence |
| `topic/digital-gardens` | Digital garden concepts |
| `topic/web-development` | Web development |
| `topic/learning` | Learning techniques |
| `topic/productivity` | Productivity systems |

**Creating New Topics:**
- Use singular form: `topic/tool` not `topic/tools`
- Be specific: `topic/rust` better than `topic/programming`
- Keep consistent: Don't use `topic/ai` and `topic/artificial-intelligence`

**Examples:**
```yaml
# Single topic
tags:
  - type/evergreen
  - topic/zettelkasten

# Multiple topics
tags:
  - type/post
  - topic/rust
  - topic/learning
  - topic/web-development
```

---

## Optional Tag Namespaces

### Maturity Namespace (`maturity/*`)

**Purpose:** Track development state of Evergreen notes

**Usage:** Evergreen notes only

**Values:**

| Tag | Icon | Meaning |
|-----|------|---------|
| `maturity/sprout` | 🌱 | Early thoughts, rough notes |
| `maturity/sapling` | 🌿 | Developing ideas, needs work |
| `maturity/tree` | 🌳 | Well-developed, stable concept |

**Also set in frontmatter:**
```yaml
maturity: "sprout"
tags:
  - type/evergreen
  - topic/pkm
  - maturity/sprout  # Optional but recommended
```

**Example Evolution:**
```yaml
# Version 1 - Initial note
maturity: "sprout"
tags:
  - maturity/sprout

# Version 2 - After refinement
maturity: "sapling"
tags:
  - maturity/sapling

# Version 3 - Mature note
maturity: "tree"
tags:
  - maturity/tree
```

---

### Status Namespace (`status/*`)

**Purpose:** Mirror project status field for filtering

**Usage:** Projects only (optional)

**Values:**

| Tag | Meaning |
|-----|---------|
| `status/idea` | Conceptual stage |
| `status/active` | Currently working |
| `status/paused` | On hold |
| `status/archived` | Completed or discontinued |

**Use with frontmatter:**
```yaml
status: "active"
tags:
  - type/project
  - topic/quartz
  - status/active  # Mirrors status field
```

---

### Series Namespace (`series/*`)

**Purpose:** Group related posts into a series

**Usage:** Blog posts (optional)

**Values:**
- Descriptive series name in kebab-case
- Examples: `series/digital-garden`, `series/rust-journey`, `series/weekly-notes`

**Example:**
```yaml
tags:
  - type/post
  - topic/rust
  - series/rust-journey

# Also in frontmatter
series: "rust-journey"
```

**Organizing Series:**
- Create an index note for the series
- Link posts in chronological order
- Tag all posts with same `series/*` tag

---

## Tag Requirements by Content Type

### Evergreen Notes

**Required:**
```yaml
tags:
  - type/evergreen          # Exactly 1
  - topic/<something>       # At least 1, can be multiple
```

**Optional:**
```yaml
tags:
  - maturity/sprout         # Recommended
```

**Complete Example:**
```yaml
tags:
  - type/evergreen
  - topic/zettelkasten
  - topic/pkm
  - topic/note-taking
  - maturity/tree
```

---

### Blog Posts

**Required:**
```yaml
tags:
  - type/post               # Exactly 1
  - topic/<something>       # At least 1, can be multiple
```

**Optional:**
```yaml
tags:
  - series/<name>           # If part of a series
```

**Complete Example:**
```yaml
tags:
  - type/post
  - topic/quartz
  - topic/digital-gardens
  - topic/web-development
  - series/digital-garden
```

---

### Projects

**Required:**
```yaml
tags:
  - type/project            # Exactly 1
  - topic/<something>       # At least 1, can be multiple
```

**Optional:**
```yaml
tags:
  - status/active           # Mirror frontmatter status
```

**Complete Example:**
```yaml
tags:
  - type/project
  - topic/quartz
  - topic/pkm
  - topic/ai
  - status/active
```

---

### Profile

**Required:**
```yaml
tags:
  - type/profile            # Exactly 1
```

**Optional:** None (topic tags don't make sense for profile)

---

## Tag Validation

### Pre-Publish Checklist

Before setting `publish: true`:

- [ ] Exactly ONE `type/*` tag present
- [ ] At least ONE `topic/*` tag (except Profile)
- [ ] All tags use proper format: `namespace/value`
- [ ] All tags are lowercase
- [ ] All multi-word values use kebab-case
- [ ] No duplicate tags
- [ ] Optional namespace tags match frontmatter fields

### Common Mistakes

**❌ No namespace:**
```yaml
tags:
  - evergreen    # Should be: type/evergreen
  - rust         # Should be: topic/rust
```

**❌ Multiple type tags:**
```yaml
tags:
  - type/evergreen
  - type/post    # ERROR: Only one type tag!
```

**❌ No topic tags:**
```yaml
tags:
  - type/evergreen
  # ERROR: Need at least one topic/* tag
```

**❌ Wrong case:**
```yaml
tags:
  - type/Evergreen       # Should be lowercase
  - topic/Rust-Lang      # Should be lowercase
```

**❌ Spaces in tags:**
```yaml
tags:
  - topic/rust programming   # Should be: topic/rust-programming
```

---

## Tag Discovery & Evolution

### Adding New Topics

When you encounter a new topic:

1. Check existing `topic/*` tags first
2. Use specific over general
3. Add to common topics list above
4. Use consistently across content

**Example:**

```markdown
# Before adding new topic
tags:
  - topic/programming       # Too general

# After adding specific topic
tags:
  - topic/rust              # Specific language
```

### Tag Cleanup

Periodically review tags:

```bash
# List all tags
grep -r "^  - topic/" content/ | sort | uniq

# Find similar tags that should merge
# topic/ai vs topic/artificial-intelligence
# topic/pkm vs topic/knowledge-management
```

**Consolidation:**
- Choose canonical tag
- Update all content
- Document in retrospective

---

## Tag Pages in Quartz

### Automatic Generation

Quartz creates tag pages at `/tags/<namespace>/<value>/`:

- `/tags/type/evergreen/` - All evergreen notes
- `/tags/topic/rust/` - All Rust content
- `/tags/maturity/tree/` - Mature evergreen notes
- `/tags/series/digital-garden/` - Digital garden series posts

### Tag Index

Main tag index at `/tags/` shows all tags grouped by namespace.

---

## Examples

### Well-Tagged Evergreen Note

```yaml
---
title: "Zettelkasten Method"
description: "A personal knowledge management system using interconnected atomic notes."
tags:
  - type/evergreen
  - topic/zettelkasten
  - topic/pkm
  - topic/note-taking
  - maturity/tree
maturity: "tree"
draft: false
publish: true
---
```

### Well-Tagged Blog Post

```yaml
---
title: "Learning Rust: Week 1"
description: "My first week learning Rust, focusing on ownership and borrowing."
tags:
  - type/post
  - topic/rust
  - topic/learning
  - series/rust-journey
date: 2026-01-15
series: "rust-journey"
draft: false
publish: true
---
```

### Well-Tagged Project

```yaml
---
title: "Quartzsite"
description: "A public digital garden built with Quartz v4."
tags:
  - type/project
  - topic/quartz
  - topic/digital-gardens
  - topic/pkm
  - status/active
status: "active"
draft: false
publish: true
---
```

---

## Quick Reference

### Tag Format Rules

- ✅ `namespace/value`
- ✅ Lowercase
- ✅ Kebab-case
- ❌ No spaces
- ❌ No capital letters
- ❌ No underscores

### Required Tags

| Content Type | Required Tags |
|--------------|---------------|
| Evergreen | `type/evergreen` + ≥1 `topic/*` |
| Post | `type/post` + ≥1 `topic/*` |
| Project | `type/project` + ≥1 `topic/*` |
| Profile | `type/profile` only |

### Optional Tags

| Namespace | Usage |
|-----------|-------|
| `maturity/*` | Evergreen notes |
| `status/*` | Projects |
| `series/*` | Blog posts |

---

*Tags are your content's navigation system. Use them thoughtfully and consistently.*
