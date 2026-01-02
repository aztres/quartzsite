---
title: "Retrospectives for Knowledge Retention"
description: "Turning ephemeral AI coding sessions into institutional memory through structured retrospectives."
tags:
  - type/evergreen
  - topic/ai
  - topic/knowledge-management
  - topic/documentation
maturity: "sapling"
draft: false
publish: true
---

# Retrospectives for Knowledge Retention

Retrospectives for Knowledge Retention is a pattern for capturing learnings from AI-assisted work sessions, transforming ephemeral context into persistent institutional memory.

## The Problem

AI coding sessions are ephemeral by default:
- Context resets between sessions
- Learnings evaporate when chat ends
- Same mistakes repeated
- Patterns discovered then forgotten

By session 10, you're re-explaining things you taught the AI in session 3.

## The Solution

After complex work, have the AI write a **structured retrospective** documenting:
- What worked and why
- What failed and the correct approach
- Patterns to reuse
- Anti-patterns to avoid
- Technical decisions made

Next session, the AI reads its own notes.

## Structure

### Minimal Template

```markdown
## Session: [Date] - [Topic]

### What We Built
- Feature 1
- Feature 2

### What Worked
- Pattern that succeeded
- Why it worked

### What Didn't Work
- Approach that failed
- Why it failed
- Correct approach discovered

### Patterns to Reuse
- [Code pattern with example]

### Next Session
- [ ] Task 1
- [ ] Task 2
```

### Comprehensive Template

See [.claude/SESSION-RETROSPECTIVE-TEMPLATE.md](https://github.com/aztres/quartzsite/blob/v4/.claude/SESSION-RETROSPECTIVE-TEMPLATE.md) for the full structure.

## Storage

```
.claude/retrospectives/
├── 2026-01-02-initial-deployment.md
├── 2026-01-05-content-system.md
├── 2026-01-10-skill-creation.md
└── README.md  # Index of retrospectives
```

## When to Create

### Triggers

Create a retrospective when:
- **End of major feature** - Significant functionality completed
- **After complex debugging** - Hard problem solved
- **Context switch** - Switching to different area of codebase
- **Weekly reviews** - Every Friday, document the week
- **Before long break** - Capture state before stepping away

### Not Needed For

Skip retrospectives for:
- Trivial tasks (typo fixes, one-line changes)
- Exploratory work with no conclusions
- Failed experiments with no learnings

## What to Capture

### Technical Decisions

**Example:**
```markdown
## Frontmatter Publishing Semantics

**Decision:** Require BOTH draft=false AND publish=true for content to be published

**Why:**
- draft alone is ambiguous (draft of what?)
- publish alone doesn't indicate readiness
- Both together is explicit intent

**Alternatives Considered:**
- Single publish field (rejected: doesn't capture draft state)
- Three-state enum (rejected: more complex than needed)
```

### Failed Approaches

**Example:**
```markdown
## Failed: Inline Validation in Templates

**What we tried:** Put validation logic inside content templates

**Why it failed:**
- Templates got bloated
- Validation logic duplicated
- Hard to update rules

**Correct approach:**
- Separate validation into quality-checklist.md
- Templates remain clean
- Single source of truth for rules
```

### Discovered Patterns

**Example:**
```markdown
## Pattern: Skills > Prompts

**Context:** Kept re-explaining frontmatter requirements to Claude

**Discovery:** Encode rules as .claude/skills/ instead of prompting

**Implementation:**
- Created content-manager skill
- Defined frontmatter contracts
- Added validation rules

**Result:** Never explain frontmatter again. Violations automatically blocked.

**Reuse:** Any domain with repeated rules → create a skill
```

## Benefits

### For AI

Next session, Claude:
- Reads retrospectives from previous sessions
- Knows what patterns worked
- Avoids known anti-patterns
- Continues from where it left off

### For Humans

Future you:
- Remembers why decisions were made
- Finds patterns to reuse in other projects
- Onboards others faster
- Debugs issues (check retrospectives for similar problems)

### For Teams

New contributors:
- Learn project patterns
- Understand architectural decisions
- See what was tried and didn't work
- Avoid repeating failed experiments

## Integration with Other Patterns

### Updates Skills

Retrospectives feed back into [[claude-skills-pattern|skills]]:

```markdown
# Retrospective discovers new pattern
"Always link blog posts to evergreen notes"

# Update linking-strategy.md in skill
Add rule: Blog posts MUST link ≥1 evergreen note
```

### Informs Documentation

Retrospectives identify documentation gaps:

```markdown
# Retrospective notes confusion
"Took 30 minutes to figure out deployment flow"

# Update claude.md
Add "Quick Start" section with deployment steps
```

### Builds Institutional Memory

Over time, retrospectives become:
- **Pattern library** - Reusable solutions
- **Decision log** - Why things are the way they are
- **Anti-pattern catalog** - What not to do
- **Onboarding material** - How the system evolved

## Example: Quartzsite Retrospectives

In [[quartzsite]], retrospectives captured:

**Session 1: Deployment**
- Node.js version requirement (22+)
- GitHub Actions setup
- Error-driven iteration pattern

**Session 2: Content System**
- Frontmatter contract discovery
- Tag taxonomy development
- Linking strategy emergence

**Session 3: Skill Creation**
- Skills > prompts realization
- Reference documentation structure
- Quality checklist pattern

Each retrospective:
- Informed the next session
- Updated relevant skills
- Added to [[documentation-as-architecture|architectural documentation]]

## Related Concepts

- [[claude-skills-pattern]] - What retrospectives update
- [[documentation-as-architecture]] - Where retrospectives feed back
- [[institutional-memory]] - What retrospectives build
- [[continuous-learning]] - How knowledge compounds

## Projects

- [[quartzsite]] - Uses retrospectives to evolve content-manager skill
- [[quantized-me]] - Planning retrospective process for vault development

## Further Reading

- [.claude/RETROSPECTIVE-PROCESS.md](https://github.com/aztres/quartzsite/blob/v4/.claude/RETROSPECTIVE-PROCESS.md) - Full process guide
- [[2026-01-02-ai-native-documentation]] - How this pattern emerged

---

*Retrospectives turn "what just happened" into "what we learned." Write them while the learning is fresh.*
