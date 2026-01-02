---
title: "Building AI-Native Documentation: From Chatbot to Build System"
description: "How I transformed AI assistance from ad-hoc prompting to a structured build system with skills, documentation architecture, and self-correcting workflows."
tags:
  - type/post
  - topic/ai
  - topic/documentation
  - topic/workflow
  - topic/quartz
date: 2026-01-02
draft: false
publish: true
---

# Building AI-Native Documentation: From Chatbot to Build System

Most developers treat AI as a chatbot—type a question, get an answer, repeat. I spent 90 minutes building something different: an AI documentation system that turns Claude Code from a helpful assistant into part of my build pipeline.

This is the story of deploying a Quartz-based digital garden to GitHub Pages, not by explaining everything manually, but by encoding the rules so the AI can't break them even if it tries.

## The Problem: Ephemeral Context

AI coding sessions are ephemeral by default. Context resets between sessions. Learnings evaporate. Every new task requires re-explaining:
- Project structure
- Build commands
- Deployment workflow
- Content standards
- Quality requirements

By the third session, you're copy-pasting the same context. By the tenth, you're spending more time on explanations than actual work.

## The Solution: Documentation as Architecture

I built a three-layer documentation system for my Quartz site:

### 1. Root claude.md - Project Context

High-level overview that Claude reads first:
- Tech stack (Quartz v4, Node.js, GitHub Pages)
- Build commands and deployment flow
- Folder structure and conventions
- Performance guidelines

Think of this as the README for your AI assistant.

### 2. .claude/skills/ - Domain Rules as Code

This is where it gets interesting. Instead of prompting "make sure frontmatter is correct," I created a [[claude-skills-pattern|content-manager skill]] that **enforces** frontmatter contracts:

```yaml
# Published only when BOTH are true
draft: false
publish: true

# Required tags
tags:
  - type/evergreen
  - topic/something
```

The skill contains:
- Templates for each content type (Blog, Evergreen notes, Projects, Profile)
- Validation rules that run before publishing
- Linking strategy (blog posts → evergreen notes, projects → related posts)
- Quality checklist Claude must pass

**Skills > prompts.** A skill isn't a suggestion—it's a constraint system.

### 3. .claude/retrospectives/ - Institutional Memory

After complex work, Claude writes a structured retrospective:
- What worked and why
- What failed and the correct approach
- Patterns to reuse
- Anti-patterns to avoid

Next session, it reads its own notes. This turns short-term context into long-term institutional memory.

## Real-World Example: Self-Correcting Deployment

When deploying Quartz to GitHub Pages, the workflow failed three times:

**Failure 1:** Node.js version mismatch (v20 vs v22)
- Claude read the error log
- Cross-referenced Quartz documentation
- Updated workflow to Node 22
- Triggered re-deployment

**Failure 2:** YAML syntax error (line break formatting)
- Detected malformed workflow file
- Fixed syntax
- Re-ran deployment

**Failure 3:** Success (1m 0s build time)

I didn't manually debug any of this. Claude:
1. Read GitHub Actions logs
2. Searched Quartz docs for requirements
3. Updated `.github/workflows/deploy.yml`
4. Verified the fix worked

This is **error-driven development as a workflow**, not a failure mode.

## The .claude/skills/ Pattern in Action

Here's how the content-manager skill works in practice:

**Me:** "Create an evergreen note about Zettelkasten"

**Claude (internally):**
1. Reads [[content-manager-skill]]
2. Checks template for evergreen notes
3. Generates proper frontmatter:
   ```yaml
   title: "Zettelkasten Method"
   description: "Personal knowledge management using atomic notes."
   tags:
     - type/evergreen
     - topic/pkm
     - topic/note-taking
   maturity: "sprout"
   draft: false
   publish: true
   ```
4. Adds required sections (Core Idea, Examples, Related Concepts)
5. Creates wiki-links to related notes
6. Runs quality checklist
7. Only sets `publish: true` when all checks pass

**Result:** Consistent content without gatekeeping every commit.

## From Documentation to Build System

Once you treat AI as a programmable collaborator with constraints, it stops being "the thing that writes code" and starts being **part of your build system**:

- Skills enforce invariants before anything gets published
- [[documentation-as-architecture|Documentation]] teaches the AI how to deploy
- [[retrospectives-for-knowledge-retention|Retrospectives]] preserve patterns across sessions
- Error logs are first-class workflow inputs

My deployment pipeline now assumes iteration, not one-shot success. When GitHub Actions fails, Claude reads the logs and patches the config. When content is created, the skill validates it against the schema. When I start a new session, retrospectives provide context.

## The Real ROI

**Setup time:** 90 minutes to build the documentation system (claude.md, skills, templates, retrospectives)

**Payback:** After the third session

Every new feature now takes 15 minutes instead of 30 minutes of context explanation + 15 minutes of work. Claude knows my tagging taxonomy, frontmatter schema, and deployment flow without me pasting it into chat.

The setup time compounds. Session four is faster than session three. Session ten is faster than session four.

## Key Patterns

If you want to move from "prompt and pray" to structured AI workflows, start with these patterns:

1. **[[claude-skills-pattern|Skills > Prompts]]** - Encode domain rules as structured skills, not ad-hoc prompts
2. **[[documentation-as-architecture]]** - Treat docs as system design, not just reference material
3. **[[retrospectives-for-knowledge-retention]]** - Turn ephemeral sessions into institutional memory
4. **Self-Correcting Workflows** - Design for iteration; AI reads error logs and patches configs
5. **[[content-governance-via-code]]** - Encode rules so AI can't bypass quality standards

## What This Enables

With this foundation, I can now:

- Create content types (blog posts, evergreen notes, projects) with guaranteed consistency
- Deploy changes with `git push` (workflow handles the rest)
- Resume work across sessions without re-explaining context
- Validate quality before publishing (automatic checklist)
- Evolve the system (skills update based on retrospectives)

The [[quartzsite|Quartz site]] you're reading was built using this system. Every page follows the same frontmatter schema. Every link follows the same strategy. Every deployment uses the same workflow.

Not because I checked each one manually, but because the [[content-manager-skill|skill]] enforces it.

## Next Steps

I'm expanding this pattern to my [[quantized-me|Obsidian vault project]], where:
- Skills encode plugin architecture patterns
- The vault itself becomes queryable via MCP
- Content and code share the same governance system

The goal: [[vault-as-product|ship vaults as products]], not just collections of notes.

## Related

**Evergreen notes:**
- [[claude-skills-pattern]] - Encoding domain rules as structured skills
- [[documentation-as-architecture]] - Docs as system design
- [[retrospectives-for-knowledge-retention]] - Building institutional memory
- [[content-governance-via-code]] - Quality through constraints
- [[vault-as-product]] - Productizing Obsidian vaults

**Projects:**
- [[quartzsite]] - This digital garden (built with the system described here)
- [[quantized-me]] - Obsidian vault with AI integration

---

*This post describes the actual implementation documented in [claude.md](https://github.com/aztres/quartzsite/blob/v4/claude.md) and [.claude/skills/content-manager/](https://github.com/aztres/quartzsite/tree/v4/.claude/skills/content-manager) in the quartzsite repository.*
