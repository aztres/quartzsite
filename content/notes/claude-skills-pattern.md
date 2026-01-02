---
title: "Claude Skills Pattern"
description: "Encoding domain rules as structured skills instead of ad-hoc prompts for AI-assisted development."
tags:
  - type/evergreen
  - topic/ai
  - topic/documentation
  - topic/workflow
maturity: "sapling"
draft: false
publish: true
---

# Claude Skills Pattern

The Claude Skills Pattern is an approach to AI-assisted development where domain knowledge and validation rules are encoded as structured "skills" rather than relying on ad-hoc prompting.

## Core Principle

**Skills > Prompts**

Instead of repeatedly explaining rules to AI assistants ("make sure frontmatter is correct", "follow naming conventions"), you create a skill file that encodes those rules as enforceable constraints.

## What is a Skill?

A skill is a structured guide for Claude Code containing:

- **Templates** - Pre-defined structures for common tasks
- **Validation rules** - Quality checks that must pass
- **Workflows** - Step-by-step processes to follow
- **Constraints** - Non-negotiable requirements
- **Examples** - Reference implementations

## Structure

```
.claude/skills/<skill-name>/
├── SKILL.md                    # Main skill definition
└── reference/
    ├── templates.md            # Reusable templates
    ├── validation.md           # Quality checks
    └── examples.md             # Reference implementations
```

## Example: Content Manager Skill

For managing a [[quartz-digital-garden]], a content-manager skill enforces:

```yaml
# Frontmatter contract
title: "Required"
description: "Required"
tags:
  - type/evergreen    # Exactly one type tag
  - topic/something   # At least one topic tag
draft: false          # Required
publish: true         # Required

# Publishing rule
# ONLY published when: draft=false AND publish=true
```

The AI **cannot** create content that violates these rules. The skill acts as a constraint system.

## Skills vs. Documentation

| Aspect | Traditional Docs | Skills |
|--------|-----------------|--------|
| **Purpose** | Reference | Enforcement |
| **AI reads it** | Sometimes | Always |
| **Violations** | Suggested fix | Blocked |
| **Evolution** | Manual updates | Self-documenting |
| **Scope** | General guidance | Specific workflows |

## Benefits

### Consistency Without Gatekeeping

You don't need to review every AI-generated file. The skill ensures standards are met before anything is created.

### Context Persistence

Skills are read every session. You don't re-explain the same rules repeatedly.

### Scalability

Add new content types by extending the skill. The validation logic applies automatically.

### Self-Documenting

Skills capture "how we do things" in machine-readable format. They evolve based on [[retrospectives-for-knowledge-retention]].

## When to Use

Create a skill when:

- You explain the same rules repeatedly
- Quality depends on following specific patterns
- Multiple people/sessions need consistent behavior
- Violations are costly (broken builds, invalid data)

## Implementation Patterns

### Minimal Skill

```markdown
# Skill Name

## Purpose
What this skill does and when to use it

## Rules
- Rule 1
- Rule 2

## Templates
[Template content]

## Validation
- [ ] Check 1
- [ ] Check 2
```

### Advanced Skill

Include:
- Multiple reference documents
- Detailed validation checklists
- Quality standards
- AI usage guidelines
- Integration with other systems

See [[content-manager-skill]] for a comprehensive example.

## Related Concepts

- [[documentation-as-architecture]] - Treating docs as system design
- [[content-governance-via-code]] - Encoding rules vs. relying on discipline
- [[retrospectives-for-knowledge-retention]] - Updating skills based on learnings
- [[ai-native-development]] - Designing workflows for AI collaboration

## Projects Using This Pattern

- [[quartzsite]] - Content management via skills
- [[quantized-me]] - Obsidian plugin architecture skills

## Further Reading

- [.claude/skills/content-manager/](https://github.com/aztres/quartzsite/tree/v4/.claude/skills/content-manager) - Real implementation
- [[2026-01-02-ai-native-documentation]] - How this pattern emerged

---

*Skills are constraints that free you from repetitive explanation. Build them once, enforce them always.*
