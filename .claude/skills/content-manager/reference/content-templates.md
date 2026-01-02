# Content Templates

Concrete Markdown templates for each first-class content type.

---

## Evergreen Note Template

```markdown
---
title: "Concept Title"
description: "A concise 1-2 sentence explanation of this concept."
tags:
  - type/evergreen
  - topic/your-topic
maturity: "sprout"
draft: false
publish: true
---

# Concept Title

Brief introduction explaining what this concept is and why it matters.

## Core Idea

The main explanation of the concept. Keep it focused and clear.

## Key Points

- Point one
- Point two
- Point three

## Examples

Concrete examples that illustrate the concept in practice.

## Related Concepts

- [[other-evergreen-note]] - How it relates
- [[another-concept]] - Connection explained

## Projects

Where this concept is used or applied:

- [[project-name]] - Brief context

## References

- External sources, papers, books
- Links to original ideas

---

*Note maturity: sprout → sapling → tree as this note evolves*
```

---

## Blog Post Template

```markdown
---
title: "Post Title"
description: "A compelling 1-2 sentence summary that makes people want to read."
tags:
  - type/post
  - topic/your-topic
date: 2026-01-02
draft: false
publish: true
---

# Post Title

Opening hook or context-setting paragraph. Why does this topic matter right now?

## Background

Context or motivation for this post. What prompted you to write this?

## Main Content

The core of your post. Use subsections as needed:

### Subsection 1

Content here...

### Subsection 2

Content here...

## Key Takeaways

- Main point one
- Main point two
- Main point three

## What's Next

Where you're going with this idea or what you plan to explore.

## Related

**Evergreen notes:**
- [[concept-one]] - How it connects
- [[concept-two]] - Why it's relevant

**Projects:**
- [[project-name]] - If applicable

---

*Published on 2026-01-02*
```

---

## Project Template

```markdown
---
title: "Project Name"
description: "What this project is and why it exists."
tags:
  - type/project
  - topic/your-domain
status: "active"
draft: false
publish: true
---

# Project Name

One-paragraph elevator pitch: what this project is, who it's for, and why it matters.

## Overview

More detailed explanation of the project's purpose, goals, and current state.

## Status: Active

Current state of the project:
- What's working now
- What's in progress
- What's planned next

## Key Features

- Feature one
- Feature two
- Feature three

## Tech Stack

List technologies, frameworks, or tools used.

## Timeline

- **Started:** YYYY-MM-DD
- **Current Phase:** Description
- **Next Milestone:** What's coming

## Challenges & Learnings

What you've learned while building this. Problems solved, insights gained.

## Related Notes

Evergreen concepts that inform this project:
- [[concept-one]] - Why it's relevant
- [[concept-two]] - How it's applied

## Related Posts

Blog posts about this project:
- [[YYYY-MM-DD-post-slug]] - Brief description
- *(Can be empty if no posts yet)*

## Links

- [Live Demo](https://example.com) (if applicable)
- [GitHub Repo](https://github.com/user/repo) (if public)
- [Documentation](https://docs.example.com) (if applicable)

---

*Status updated: 2026-01-02*
```

---

## Profile Template

```markdown
---
title: "Your Name"
description: "Short bio describing who you are and what you do."
tags:
  - type/profile
layout: "profile"
draft: false
publish: true
---

# Hi, I'm Your Name

Brief introduction paragraph. Who you are, what you do, what you're interested in.

## About Me

2-3 paragraphs expanding on:
- Your background
- What you're passionate about
- What you're working on
- What this site is for

## Currently Working On

Active projects I'm focused on:

- [[project-one]] - Brief description
- [[project-two]] - Brief description
- [[project-three]] - Brief description

## Interests & Expertise

Topics I write about and explore:

- **Topic Area 1** - What you focus on here
- **Topic Area 2** - What you explore
- **Topic Area 3** - What you're learning

## Find Me Online

- **Email:** your@email.com
- **GitHub:** [github.com/username](https://github.com/username)
- **Twitter/X:** [@handle](https://twitter.com/handle)
- **LinkedIn:** [linkedin.com/in/profile](https://linkedin.com/in/profile)
- **Mastodon:** [@handle@instance.social](https://instance.social/@handle)

## Recent Posts

- [[YYYY-MM-DD-recent-post]] - Brief description
- [[YYYY-MM-DD-another-post]] - Brief description
- [View all posts](/posts/)

## How I Work

Brief explanation of your workflow, tools, or philosophy that makes your approach unique.

---

*This site is built with [Quartz](https://quartz.jzhao.xyz) and updated regularly.*
```

---

## Usage Notes

### Choosing a Template

When Claude receives a content creation request:

1. **Identify the type** from user's intent
2. **Copy the appropriate template** from above
3. **Fill in required frontmatter** fields
4. **Replace placeholder content** with actual content
5. **Add wiki-links** following linking strategy
6. **Validate** against quality checklist

### Customizing Templates

These templates are starting points. Customize them as patterns emerge:

- Add new sections that prove useful
- Remove sections that don't fit your style
- Adjust formality/tone to match your voice
- Update examples based on actual usage

### Template Evolution

As you use these templates, update them based on retrospective learnings:

- Capture successful patterns
- Remove unused sections
- Add sections that keep appearing
- Document template variations for special cases
