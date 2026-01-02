# Linking Strategy

Details how Blog, Evergreen, Projects, and Profile should interlink, including examples of "Related" sections and project hubs.

---

## Linking Philosophy

**Public second brain linking follows these principles:**

1. **Bi-directional Discovery:** Links create two-way pathways for readers
2. **Context Over Quantity:** Quality links with context > many bare links
3. **Progressive Depth:** Surface content leads to deeper evergreen notes
4. **Project Hubs:** Projects aggregate related content

---

## Wiki-Link Syntax

### Basic Link

```markdown
[[target-slug]]
```

**Examples:**
- `[[zettelkasten-method]]` → Links to notes/zettelkasten-method.md
- `[[2026-01-02-first-post]]` → Links to posts/2026-01-02-first-post.md
- `[[quartzsite]]` → Links to projects/quartzsite.md

### Link with Custom Text

```markdown
[[target-slug|Custom Link Text]]
```

**Examples:**
- `[[zettelkasten-method|Zettelkasten]]`
- `[[2026-01-02-first-post|my first post]]`
- `[[quartzsite|this project]]`

### Link with Folder Path

```markdown
[[folder/target-slug]]
```

**Examples:**
- `[[notes/atomic-notes]]`
- `[[posts/2026-01-02-first-post]]`
- `[[projects/quartzsite]]`

**Note:** Quartz usually resolves links without folder paths, but be explicit when there might be ambiguity.

---

## Linking Patterns by Type

### Blog Posts → Other Content

**Always link to:**
- At least 1 Evergreen note that provides deeper context
- The Project page if post is about a specific project

**Structure:**

```markdown
# Post Title

Opening paragraph mentioning [[core-concept]] I'm exploring...

## Main Content

Discussion of the topic, referencing [[related-evergreen-note]]...

When building [[my-project]], I discovered...

## Related

**Evergreen notes:**
- [[concept-one]] - Why this concept matters here
- [[concept-two]] - How it connects to the post topic
- [[concept-three]] - Deeper dive into this idea

**Projects:**
- [[project-name]] - If the post relates to a specific project

**Further reading:**
- External links or resources
```

**Example:**

```markdown
# Building a Digital Garden with Quartz

I've been exploring [[digital-gardens]] and decided to build my own using
[[quartz-framework]]. This post documents what I learned.

## Why Quartz?

After researching [[static-site-generators]], I chose Quartz because...

## The Build Process

While building [[quartzsite]], I discovered several key patterns...

## Related

**Evergreen notes:**
- [[digital-gardens]] - What digital gardens are and why they matter
- [[public-learning]] - The philosophy behind learning in public
- [[quartz-framework]] - Deep dive into Quartz features

**Projects:**
- [[quartzsite]] - My digital garden project

**Further reading:**
- [Quartz Documentation](https://quartz.jzhao.xyz)
```

---

### Evergreen Notes → Other Content

**Always link to:**
- Other Evergreen notes that define related concepts
- Projects where this concept is applied (if any)

**Structure:**

```markdown
# Concept Title

Definition mentioning [[foundational-concept]] and [[related-concept]]...

## Core Idea

Explanation referencing [[prerequisite-concept]]...

## Examples

Concrete examples...

## Related Concepts

- [[concept-one]] - How it relates to this concept
- [[concept-two]] - Contrast or comparison
- [[concept-three]] - Next step in understanding

## Projects

Where this concept is used:

- [[project-name]] - How it's applied in this project
- [[another-project]] - Different application

## Further Reading

External sources...
```

**Example:**

```markdown
# Digital Gardens

A digital garden is a [[public-learning]] space where notes grow over time,
emphasizing [[evergreen-notes]] over chronological posts.

## Core Idea

Unlike traditional blogs, digital gardens embrace [[imperfect-notes]] and
use [[bidirectional-links]] to create knowledge networks.

## Key Characteristics

- Notes are [[work-in-progress]]
- Organization by [[topic-not-time]]
- Emphasis on [[networked-thought]]

## Related Concepts

- [[evergreen-notes]] - Long-lived notes that evolve
- [[zettelkasten-method]] - Note-taking system that inspired digital gardens
- [[public-learning]] - Philosophy of sharing learning journey
- [[second-brain]] - Personal knowledge management

## Projects

- [[quartzsite]] - My digital garden implementation
- [[content-manager-skill]] - Tool for managing garden content

## Further Reading

- [Digital Gardens (Maggie Appleton)](https://maggieappleton.com/garden-history)
```

---

### Projects → Other Content

**Always include:**
- **Related notes** section linking to Evergreen notes
- **Related posts** section linking to Blog posts (can be empty)

**Structure:**

```markdown
# Project Name

Overview mentioning key [[concepts]] this project explores...

## Overview

Detailed description...

## Status: Active

Current state...

## Key Features

Features list...

## Challenges & Learnings

What I learned about [[concept-one]] and [[concept-two]]...

## Related Notes

Concepts that inform this project:
- [[concept-one]] - Core principle applied here
- [[concept-two]] - How this concept guides the design
- [[concept-three]] - Theory behind the implementation

## Related Posts

Blog posts about this project:
- [[2026-01-02-project-launch]] - Initial announcement
- [[2026-01-15-project-update]] - Progress update
- *(Add more as you write)*

## Links

- [Live Demo](https://example.com)
- [GitHub](https://github.com/user/project)
```

**Example:**

```markdown
# Quartzsite

A public [[digital-garden]] built with [[quartz-framework]], demonstrating
[[public-learning]] and [[networked-thought]].

## Overview

Quartzsite is my personal second brain...

## Status: Active

Currently focusing on:
- Content creation using [[content-manager-skill]]
- Implementing [[evergreen-notes]] methodology
- Building interconnected knowledge with [[bidirectional-links]]

## Related Notes

Concepts driving this project:
- [[digital-gardens]] - The philosophy behind this site
- [[quartz-framework]] - Technical foundation
- [[evergreen-notes]] - Content strategy
- [[public-learning]] - Why I build in public
- [[content-manager-skill]] - Content workflow automation

## Related Posts

- [[2026-01-02-building-digital-garden]] - Project kickoff
- [[2026-01-10-content-workflows]] - Setting up the skill system

## Links

- [Live Site](https://aztres.github.io/quartzsite/)
- [GitHub](https://github.com/aztres/quartzsite)
```

---

### Profile → Other Content

**Always include:**
- Links to active projects
- Link to posts index or recent posts
- Optional links to key Evergreen notes

**Structure:**

```markdown
# Your Name

Bio intro...

## Currently Working On

- [[active-project-1]] - Brief description
- [[active-project-2]] - Brief description
- [[active-project-3]] - Brief description

## Interests & Expertise

Areas where I have [[evergreen-notes]]:
- **Topic 1** - Focus area
- **Topic 2** - Exploration area

## Recent Posts

- [[2026-01-02-recent-post]] - Brief description
- [View all posts](/posts/)

## Key Notes

Core concepts I write about:
- [[important-concept-1]]
- [[important-concept-2]]
```

---

## Link Context Best Practices

### ✅ Good Link Context

**Provide context around links:**

```markdown
I've been exploring [[digital-gardens|digital gardens]] as a way to
think with the garage door up, following the [[public-learning]]
philosophy.
```

**Why good:** Reader knows what they'll find before clicking.

### ❌ Poor Link Context

```markdown
I've been exploring [[digital-gardens]]. [[public-learning]] is good.
```

**Why poor:** Links appear random, no flow.

---

## Backlinks

**Quartz automatically generates backlinks.** Every page shows:
- "Links to this page" section
- Graph view connections

**Your responsibility:**
- Create meaningful forward links
- Quartz handles backlink display

**Leverage backlinks:**
- Check backlinks when updating notes
- Ensure bidirectional connections make sense
- Update context if backlinks seem wrong

---

## Link Maintenance

### Finding Broken Links

```bash
# Search for links to a file
grep -r "old-slug" content/

# After renaming, update all
# Before: [[old-slug]]
# After: [[new-slug]]
```

### Validating Links

Before publishing content:
1. Check all wiki-links resolve
2. Verify external links work
3. Ensure context around links is clear
4. Confirm backlinks will make sense

---

## Examples by Scenario

### Scenario: Writing About Learning Rust

**Blog Post:** `content/posts/2026-01-15-learning-rust.md`

```markdown
I'm learning [[rust-language]] by building small projects. The
[[ownership-model]] is challenging but makes sense after studying
[[memory-safety]] concepts.

## Related

**Evergreen notes:**
- [[rust-language]] - Overview of Rust and why I'm learning it
- [[ownership-model]] - Deep dive into Rust's ownership system
- [[memory-safety]] - Broader concept of safe memory management

**Projects:**
- [[rust-playground]] - My collection of Rust learning projects
```

**Evergreen Note:** `content/notes/rust-language.md`

```markdown
# Rust Language

Rust is a systems programming language emphasizing [[memory-safety]]
without garbage collection through its unique [[ownership-model]].

## Related Concepts

- [[ownership-model]] - Rust's core innovation
- [[memory-safety]] - Problem Rust solves
- [[systems-programming]] - Domain where Rust excels

## Projects

- [[rust-playground]] - Where I practice Rust
```

**Project:** `content/projects/rust-playground.md`

```markdown
# Rust Playground

Collection of small Rust projects for learning [[rust-language]],
focusing on understanding the [[ownership-model]].

## Related Notes

- [[rust-language]] - Language overview
- [[ownership-model]] - Core concept I'm mastering
- [[learning-by-doing]] - My learning philosophy

## Related Posts

- [[2026-01-15-learning-rust]] - Why I'm learning Rust
- [[2026-02-01-rust-ownership-aha]] - When ownership clicked
```

---

## Quick Reference

### Link Goals by Type

| From → To | Goal | Example |
|-----------|------|---------|
| Post → Evergreen | Provide deeper context | Post about learning → [[concept]] note |
| Post → Project | Show application | Post about feature → [[project]] using it |
| Evergreen → Evergreen | Build concept network | [[rust]] → [[ownership-model]] |
| Evergreen → Project | Show real usage | [[concept]] → [[project]] applying it |
| Project → Evergreen | Document foundations | [[project]] → [[concepts]] behind it |
| Project → Post | Tell the story | [[project]] → [[posts]] about progress |
| Profile → Projects | Showcase work | Profile → active [[projects]] |
| Profile → Posts | Share thoughts | Profile → recent [[posts]] |

---

*Good linking turns isolated notes into a knowledge network. Every link is a pathway for discovery.*
