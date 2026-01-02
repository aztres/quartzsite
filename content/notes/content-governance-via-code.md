---
title: "Content Governance via Code"
description: "Enforcing content quality through code constraints rather than relying on discipline and manual review."
tags:
  - type/evergreen
  - topic/content
  - topic/governance
  - topic/automation
maturity: "sapling"
draft: false
publish: true
---

# Content Governance via Code

Content Governance via Code is the practice of encoding content quality rules as enforceable constraints in code, rather than relying on discipline, guidelines, or manual gatekeeping.

## Core Principle

**Don't rely on discipline—encode the rules.**

Instead of hoping people follow style guides, create a system where invalid content cannot be published.

## How It Works

### Traditional Governance

```
Writer creates content
  ↓
Editor reviews manually
  ↓
Checks style guide
  ↓
Suggests fixes
  ↓
Writer revises
  ↓
(repeat until correct)
  ↓
Published
```

**Problem:** Expensive, slow, doesn't scale

### Code-Based Governance

```
Writer creates content
  ↓
System validates automatically
  ↓
Violations blocked OR auto-fixed
  ↓
Published (only if valid)
```

**Benefit:** Fast, consistent, scales infinitely

## Implementation Patterns

### 1. Frontmatter Contracts

Define required fields and validation rules:

```yaml
# Valid content
title: "Post Title"       # Required
description: "Summary"    # Required
tags:
  - type/post            # Exactly one type/*
  - topic/something      # At least one topic/*
draft: false             # Required
publish: true            # Required

# Publishing rule
# ONLY published when: draft=false AND publish=true
```

The system **cannot** create content missing these fields.

### 2. Tag Taxonomies

Enforce tag structure via [[claude-skills-pattern|skills]]:

```yaml
# Valid tags
tags:
  - type/evergreen      # namespace/value format
  - topic/ai            # lowercase, kebab-case
  - maturity/sapling    # controlled vocabulary

# Invalid tags (blocked)
tags:
  - evergreen           # Missing namespace
  - Topic/AI            # Wrong case
  - type/blog-post      # Invalid value for type/*
```

### 3. Linking Strategies

Enforce relationship patterns:

```markdown
# Blog posts MUST link to evergreen notes
[[evergreen-concept]] mentioned in introduction

## Related
- [[concept-one]] - Context
- [[concept-two]] - Related idea

# Projects MUST have these sections
## Related Notes
## Related Posts
```

The [[content-manager-skill]] enforces these linking rules.

### 4. Quality Checklists

Automated validation before publish:

```
✓ Frontmatter complete
✓ Tags valid
✓ At least one outbound link
✓ Description under 160 chars
✓ No placeholder text
✓ No broken wiki-links
```

Content only publishes when all checks pass.

## Benefits

### Consistency Without Gatekeeping

You don't manually review every piece of content. The system ensures standards are met automatically.

**Example:** In [[quartzsite]], Claude Code cannot publish content that violates the frontmatter contract. I get consistency without checking every commit.

### Scalability

Add 10 pieces of content or 1000—the validation runs the same.

### Speed

No waiting for human review. Instant feedback on violations.

### Documentation

The rules ARE the documentation. Code is the source of truth.

### Evolution

Update the rules once; all future content follows the new pattern.

## Real-World Example

### Building a Digital Garden

**Problem:** Need consistent frontmatter across blog posts, evergreen notes, and project pages.

**Solution:** [[content-manager-skill]] that enforces:

1. **Type system**
   - Exactly one `type/*` tag per page
   - Valid types: evergreen, post, project, profile

2. **Publishing semantics**
   - `draft: false` + `publish: true` = published
   - Any other combo = hidden

3. **Linking strategy**
   - Blog posts → link to evergreen notes
   - Projects → list related notes and posts
   - Evergreens → link to other evergreens

4. **Quality gates**
   - Description required and under 160 chars
   - At least one topic tag
   - Valid wiki-links only

**Result:** Claude Code can't bypass the rules. Every page follows the same standards.

## When to Use

Apply governance-via-code when:

- **Volume is high** - Many pieces of content
- **Contributors vary** - Multiple people or AI assistants
- **Quality matters** - Broken content is costly
- **Consistency is required** - Brand/style guidelines
- **Manual review doesn't scale** - Too slow or expensive

## Contrast with Manual Governance

| Manual | Code-Based |
|--------|-----------|
| Review each piece | Validate automatically |
| Slow | Instant |
| Human cost | One-time setup |
| Inconsistent (fatigue) | Perfectly consistent |
| Doesn't scale | Scales infinitely |
| Guidelines suggest | Rules enforce |

## Implementation Layers

### Layer 1: Schema Validation

Validate data structure (YAML, JSON):
- Required fields present
- Correct data types
- Valid enum values

### Layer 2: Business Rules

Enforce domain logic:
- Publishing semantics
- Tag taxonomies
- Relationship patterns

### Layer 3: Quality Standards

Check content quality:
- No placeholder text
- Minimum length
- Valid links
- SEO requirements

### Layer 4: Style Enforcement

Automated formatting:
- Consistent markdown
- Heading structure
- Code block syntax
- Prose style (optional)

## Tools and Patterns

- **[[claude-skills-pattern]]** - AI enforces rules via skills
- **Schema validators** - JSON Schema, YAML validators
- **Linters** - Markdown lint, prose lint
- **Pre-commit hooks** - Block commits with violations
- **CI/CD checks** - Validate before deploy

## Related Concepts

- [[documentation-as-architecture]] - Docs as enforceable constraints
- [[claude-skills-pattern]] - Skills enforce content rules
- [[automated-quality-gates]] - Validation in build pipelines
- [[content-standards]] - What the rules enforce

## Projects

- [[quartzsite]] - Digital garden with code-based governance
  - Frontmatter validation
  - Tag taxonomy enforcement
  - Linking strategy rules

## Further Reading

- [[2026-01-02-ai-native-documentation]] - How this pattern emerged
- [.claude/skills/content-manager/](https://github.com/aztres/quartzsite/tree/v4/.claude/skills/content-manager) - Implementation

---

*Code enforcement scales. Human discipline doesn't. Choose code.*
