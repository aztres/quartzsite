# Quality Checklist

Pre-publish validation checklist Claude should run through before setting `publish: true` and `draft: false` on any page.

---

## Purpose

This checklist ensures content meets minimum quality standards before going live. Use this before:
- Setting `publish: true` and `draft: false`
- Committing content to git
- Deploying to production

---

## Universal Checks (All Content Types)

### ✅ Frontmatter Validation

- [ ] **YAML is valid** - No syntax errors
- [ ] **All required fields present** - See [frontmatter-standards.md](frontmatter-standards.md)
- [ ] **Field values are correct type** - Strings, booleans, arrays, dates
- [ ] **Title is meaningful** - Not "Untitled" or placeholder
- [ ] **Description exists** - 1-2 sentences, under 160 chars
- [ ] **Draft and publish fields set** - Both `draft: false` and `publish: true`

### ✅ Tag Validation

- [ ] **Exactly ONE type tag** - `type/evergreen` OR `type/post` OR `type/project` OR `type/profile`
- [ ] **At least ONE topic tag** - Except for Profile type
- [ ] **Tags properly formatted** - `namespace/value`, lowercase, kebab-case
- [ ] **No duplicate tags** - Each tag appears once
- [ ] **Tags match content** - Tags accurately describe the content

### ✅ Content Body

- [ ] **Not empty** - Content exists beyond template
- [ ] **Has introduction** - Opening paragraph explains what this is
- [ ] **Logical headings** - Proper `##` heading hierarchy
- [ ] **Complete sentences** - No obvious placeholders like "TODO" or "FIXME"
- [ ] **Spell-check passed** - No obvious typos (if tools available)

### ✅ Linking

- [ ] **At least one outbound link** - For Evergreen/Post/Project (not required for Profile)
- [ ] **Links are valid wiki-links** - Proper `[[target]]` or `[[target|text]]` format
- [ ] **Links have context** - Not just bare links, explained in surrounding text
- [ ] **No broken links** - All wiki-links point to existing content or planned content

### ✅ Formatting

- [ ] **Markdown is valid** - No obvious syntax errors
- [ ] **Lists formatted properly** - Bullets or numbers consistent
- [ ] **Code blocks have language** - ` ```language ` not just ` ``` `
- [ ] **No weird characters** - No control characters or encoding issues

---

## Type-Specific Checks

### Evergreen Notes

#### Required Fields
- [ ] `title` - Concept name
- [ ] `description` - 1-2 sentence summary
- [ ] `tags` - Including `type/evergreen` and ≥1 `topic/*`
- [ ] `maturity` - `sprout` | `sapling` | `tree`
- [ ] `draft: false`
- [ ] `publish: true`

#### Content Structure
- [ ] **Clear definition** - Concept is explained early
- [ ] **Core idea section** - Main explanation exists
- [ ] **Examples provided** - Concrete examples when applicable
- [ ] **Related concepts linked** - Links to other Evergreen notes
- [ ] **Projects section** - If concept is applied in projects

#### Quality Standards
- [ ] **Focused on one concept** - Not trying to cover too much
- [ ] **Atomic** - Can stand alone
- [ ] **Evergreen** - Timeless, not time-bound content
- [ ] **Links to related notes** - At least 2-3 related evergreen links

---

### Blog Posts

#### Required Fields
- [ ] `title` - Post title
- [ ] `description` - Engaging summary
- [ ] `tags` - Including `type/post` and ≥1 `topic/*`
- [ ] `date` - Format `YYYY-MM-DD`
- [ ] `draft: false`
- [ ] `publish: true`

#### File Naming
- [ ] **Filename matches date** - `YYYY-MM-DD-slug.md` matches frontmatter `date`

#### Content Structure
- [ ] **Hook/opening** - Engaging first paragraph
- [ ] **Context provided** - Why this topic now
- [ ] **Main content** - Substantial discussion
- [ ] **Takeaways** - Key points summarized
- [ ] **Related section** - Links to Evergreen notes and/or Projects

#### Quality Standards
- [ ] **Tells a story** - Has narrative flow
- [ ] **Personal voice** - Reflects your perspective
- [ ] **Links to evergreens** - At least 1 link to deeper evergreen notes
- [ ] **Substant** - Not just a stub (aim for 300+ words unless micro-post)

---

### Projects

#### Required Fields
- [ ] `title` - Project name
- [ ] `description` - What it is and why
- [ ] `tags` - Including `type/project` and ≥1 `topic/*`
- [ ] `status` - `idea` | `active` | `paused` | `archived`
- [ ] `draft: false`
- [ ] `publish: true`

#### Content Structure
- [ ] **Overview** - What the project is
- [ ] **Status section** - Current state
- [ ] **Key features** - What it does/will do
- [ ] **Related notes section** - Evergreen concepts
- [ ] **Related posts section** - Blog posts (can be empty)

#### Quality Standards
- [ ] **Clear purpose** - Reader understands what this is
- [ ] **Current status accurate** - Status field and description match
- [ ] **Links to concepts** - Connected to relevant Evergreen notes
- [ ] **External links work** - If repo/demo links exist, they're valid

---

### Profile

#### Required Fields
- [ ] `title` - Your name or site name
- [ ] `description` - Short bio
- [ ] `tags` - Only `type/profile` required
- [ ] `layout: "profile"`
- [ ] `draft: false`
- [ ] `publish: true`

#### Content Structure
- [ ] **Introduction** - Who you are
- [ ] **About section** - Background and interests
- [ ] **Currently working on** - Active projects linked
- [ ] **Contact/social** - How to reach you
- [ ] **Recent posts** - Link to posts index or recent posts

#### Quality Standards
- [ ] **Welcoming** - Approachable tone
- [ ] **Up to date** - Currently working on reflects actual focus
- [ ] **Links work** - Social links are valid
- [ ] **Personal** - Reflects your voice

---

## Pre-Commit Checklist

Before committing to git:

- [ ] **All quality checks passed** - All relevant items above checked
- [ ] **Build test passed** - `npx quartz build` succeeds locally
- [ ] **Preview looks good** - Previewed with `npx quartz build --serve`
- [ ] **Links validated** - Clicked through wiki-links in preview
- [ ] **No console errors** - No errors in browser console

---

## Common Quality Issues

### ❌ Issues to Fix Before Publishing

**Frontmatter:**
```yaml
# BAD
title: ""                    # Empty title
description: "TODO"          # Placeholder
tags:                        # Missing type tag
  - topic/something
draft: true                  # Still draft
publish: false               # Not published
```

**Content:**
```markdown
# TODO: Write title

This is a placeholder.

TODO: Add content here.

Links:
- [[broken-link]]           # Link to non-existent page
```

**Tags:**
```yaml
tags:
  - evergreen               # Missing namespace
  - type/evergreen
  - type/post               # Multiple type tags!
  - Topic/Rust              # Wrong case
```

### ✅ After Fixing

**Frontmatter:**
```yaml
title: "Clear Concept Title"
description: "Concise explanation of what this is."
tags:
  - type/evergreen
  - topic/something
maturity: "sprout"
draft: false
publish: true
```

**Content:**
```markdown
# Clear Concept Title

Opening paragraph explaining the concept...

## Core Idea

Substantive content here...

## Related

- [[existing-note]] - How it connects
```

---

## Automated Validation (Future)

**Potential automation:**

```bash
# Validate frontmatter
./scripts/validate-frontmatter.sh content/

# Check for broken wiki-links
./scripts/check-links.sh content/

# Find missing tags
./scripts/validate-tags.sh content/
```

**For now:** Manual checklist review.

---

## Quality Levels

### Minimum (Required for Publish)

- All required frontmatter fields
- Valid tags
- Non-empty content
- Basic structure (headings)
- No obvious errors

### Good (Recommended)

- All minimum requirements
- Multiple related links
- Examples provided
- Clear writing
- Spell-checked

### Excellent (Aspirational)

- All good requirements
- Rich interconnections
- Visual aids (diagrams, images)
- External references
- Polished prose

**Start with minimum, improve over time.** Evergreen notes especially benefit from iteration.

---

## Example: Checking an Evergreen Note

### Initial Draft

```yaml
---
title: "Rust"
description: ""
tags:
  - type/evergreen
maturity: "sprout"
draft: true
publish: false
---

# Rust

Notes about rust programming.

TODO: add more
```

**Checklist Results:**
- ❌ Description empty
- ❌ No topic tags
- ❌ Content is stub
- ❌ No links
- ❌ Still draft

---

### After Quality Pass

```yaml
---
title: "Rust Programming Language"
description: "A systems programming language emphasizing memory safety without garbage collection."
tags:
  - type/evergreen
  - topic/rust
  - topic/programming
  - maturity/sprout
maturity: "sprout"
draft: false
publish: true
---

# Rust Programming Language

Rust is a systems programming language that emphasizes [[memory-safety]]
and [[concurrency]] without using a garbage collector. Its unique
[[ownership-model]] prevents common bugs at compile time.

## Core Ideas

- [[ownership-model]] - Compile-time memory safety
- [[borrowing-and-lifetimes]] - Managing references
- [[fearless-concurrency]] - Safe parallel programming

## Why Rust Matters

Rust provides systems-level performance with high-level safety guarantees,
making it ideal for [[systems-programming]] where both speed and
correctness are critical.

## Related Concepts

- [[systems-programming]] - Domain where Rust excels
- [[memory-safety]] - Problem Rust solves elegantly
- [[ownership-model]] - Rust's key innovation

## Projects

- [[rust-playground]] - My Rust learning projects

## Further Reading

- [The Rust Book](https://doc.rust-lang.org/book/)
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/)
```

**Checklist Results:**
- ✅ All required frontmatter
- ✅ Topic tags present
- ✅ Substantive content
- ✅ Multiple links
- ✅ Ready to publish

---

## Usage in AI Workflows

### Claude's Responsibility

Before setting `publish: true` and `draft: false`, Claude should:

1. **Run through this checklist** mentally
2. **Fix obvious issues** automatically
3. **Flag issues that need user input** explicitly
4. **Suggest improvements** without making risky changes

### Example Dialogue

```
User: "Publish the rust note"

Claude: "Before publishing, I've checked the quality:

✅ Frontmatter complete
✅ Tags valid
✅ Content structure good
⚠️  Only 1 outbound link - recommend adding 2-3 more related concepts
⚠️  Description could be more specific

Should I:
A) Add links to [[memory-safety]] and [[systems-programming]]
B) Publish as-is
C) Keep as draft for now"
```

---

*Quality is a process, not a state. Start with the checklist, improve through iteration.*
