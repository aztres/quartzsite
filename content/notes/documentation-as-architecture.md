---
title: "Documentation as Architecture"
description: "Treating documentation as system design rather than reference material, making it structural and enforceable."
tags:
  - type/evergreen
  - topic/documentation
  - topic/architecture
  - topic/ai
maturity: "sapling"
draft: false
publish: true
---

# Documentation as Architecture

Documentation as Architecture is the practice of treating documentation not as supplementary reference material, but as a structural component of the system itself—documentation that defines, constrains, and enforces how the system works.

## Core Idea

Traditional documentation describes what exists. **Architectural documentation defines what can exist.**

Instead of:
> "Here's how the system works (please follow these guidelines)"

You create:
> "Here's how the system MUST work (violations are impossible)"

## Characteristics

### 1. Executable Truth

Architectural documentation is the source of truth that systems read and enforce.

**Example:** A `.github/workflows/deploy.yml` file is documentation that:
- Specifies build requirements (Node.js 22+)
- Defines deployment steps
- Executes automatically on push
- **Cannot** be violated (wrong version = build fails)

The workflow file is both documentation AND the deployment system.

### 2. Machine-Readable

Written for both humans and machines (AI assistants, build systems, validation tools).

**Example:** [[claude-skills-pattern|Skills]] are documentation that Claude Code reads and enforces. Frontmatter schemas are documentation that parsers validate.

### 3. Layered Structure

Different layers for different audiences and purposes:

| Layer | Purpose | Audience |
|-------|---------|----------|
| **Overview** | Context and purpose | Humans, AI |
| **Constraints** | Non-negotiable rules | Systems, AI |
| **Guidelines** | Best practices | Humans |
| **Examples** | Reference implementations | Everyone |

### 4. Self-Updating

The documentation evolves with the system. When patterns change, the documentation changes. When documentation changes, the system changes.

**Example:** [[retrospectives-for-knowledge-retention|Retrospectives]] capture what worked and update the architectural docs for future sessions.

## Implementation

### Root Documentation Layer

**Purpose:** High-level context
**Format:** `claude.md`, `README.md`
**Contains:**
- Project overview
- Tech stack
- Build commands
- Deployment flow
- Performance guidelines

This is the README for your AI assistant.

### Constraint Layer

**Purpose:** Enforceable rules
**Format:** `.claude/skills/`, `.github/workflows/`, schema files
**Contains:**
- Validation rules
- Required patterns
- Quality standards
- Workflow definitions

This is what makes violations impossible.

### Process Layer

**Purpose:** Workflows and procedures
**Format:** Templates, checklists, runbooks
**Contains:**
- Step-by-step processes
- Decision trees
- Troubleshooting guides

This is how work gets done consistently.

### Memory Layer

**Purpose:** Institutional knowledge
**Format:** `.claude/retrospectives/`, decision logs
**Contains:**
- What worked and why
- What failed and the fix
- Patterns to reuse
- Anti-patterns to avoid

This is how knowledge compounds across sessions.

## Benefits

### For AI Collaboration

AI assistants can:
- Read architectural docs to understand constraints
- Enforce rules automatically
- Resume work across sessions
- Self-correct based on error logs

### For Humans

Developers can:
- Understand system invariants
- Onboard faster (docs are executable)
- Trust automation (rules are enforced)
- Evolve patterns (docs are versioned)

### For Systems

Build systems can:
- Validate before deployment
- Document themselves (workflow files)
- Fail fast on violations
- Teach AI how to fix errors

## Contrast with Traditional Documentation

| Traditional Docs | Architectural Docs |
|-----------------|-------------------|
| "Here's how it works" | "Here's how it MUST work" |
| Optional reading | System reads it |
| Gets outdated | Self-updating |
| Describes implementation | Defines constraints |
| For humans only | For humans + machines |

## Example: Quartz Site Documentation

The [[quartzsite]] project uses three architectural layers:

**1. Context (`claude.md`)**
- Tech stack (Quartz v4, Node.js, GitHub Pages)
- Build commands: `npx quartz build --serve`
- Deployment: `git push origin v4`

**2. Constraints (`.claude/skills/content-manager/`)**
- Frontmatter contracts (draft + publish semantics)
- Tag taxonomy (type/*, topic/*)
- Linking strategy (blog → evergreen, projects → posts)
- Quality checklist

**3. Workflows (`.github/workflows/deploy.yml`)**
- Build: Node 22, npm ci, quartz build
- Deploy: GitHub Pages via Actions
- Trigger: Push to v4 branch

Claude Code reads all three layers. It **cannot** create content that violates the skill constraints. It **cannot** deploy without passing the workflow checks. It **can** resume work across sessions by reading the architectural docs.

## When to Use This Pattern

Apply documentation-as-architecture when:

- **Consistency matters** - Same output every time
- **AI collaboration is involved** - Need machine-readable rules
- **Quality is non-negotiable** - Can't afford violations
- **Context switching is expensive** - Need to resume work quickly
- **Multiple contributors** - Enforce standards automatically

## Related Concepts

- [[claude-skills-pattern]] - Encoding domain rules as structured skills
- [[content-governance-via-code]] - Quality through constraints, not discipline
- [[retrospectives-for-knowledge-retention]] - Building institutional memory
- [[workflows-as-executable-documentation]] - CI/CD workflows that teach

## Projects

- [[quartzsite]] - Digital garden with architectural documentation
- [[quantized-me]] - Obsidian vault using this pattern

## Further Reading

- [[2026-01-02-ai-native-documentation]] - How this pattern emerged in practice
- [claude.md](https://github.com/aztres/quartzsite/blob/v4/claude.md) - Example implementation

---

*Good architecture is self-documenting. Great architecture IS documentation.*
