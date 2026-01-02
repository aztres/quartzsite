# Retrospective Process Guide

## Purpose

The retrospective system creates **continuous learning** by documenting:
- What worked and why
- What failed and the correct approach
- Discoveries about Quartz and static site generation
- Patterns to reuse
- Anti-patterns to avoid

This builds **institutional memory** so future sessions benefit from past learnings.

---

## When to Run Retrospectives

### End of Major Content Work
When you've created significant content or restructured the site.

### End of Configuration Changes
When you've modified Quartz configuration or added custom components.

### End of Troubleshooting
When you've fixed build issues or deployment problems.

### Weekly Reviews
Every Friday, review the week's work and create a weekly retrospective.

---

## How to Create a Retrospective

### Step 1: Copy the Template

```bash
cp .claude/SESSION-RETROSPECTIVE-TEMPLATE.md .claude/retrospectives/YYYY-MM-DD-topic-name.md
```

### Step 2: Fill Out Each Section

Work through the template systematically:

1. **Session Overview** - High-level summary
2. **What We Built** - Content and features added
3. **Key Learnings** - What worked, what didn't, discoveries
4. **Patterns** - Reusable content and config patterns
5. **Issues** - Build problems and solutions
6. **Documentation** - What was updated
7. **Next Steps** - Immediate next actions

### Step 3: Update Project Documentation

- Update `claude.md` "Recent Updates" section
- Update `.claude/SESSION-SUMMARY.md` with completed work
- Create topic-specific memos for complex topics

---

## What Makes a Good Retrospective

### ✅ DO

**Be Specific**
- Include file paths: `content/index.md`, `quartz.config.ts`
- Show examples: frontmatter, wiki-links, config snippets
- Explain the "why" not just the "what"

**Document Failures**
- Build errors and their solutions
- Broken links and how to fix them
- Configuration mistakes and correct approach

**Extract Patterns**
- Content organization patterns
- Frontmatter templates
- Wiki-link strategies

**Link to Code/Content**
- Reference specific files
- Make it easy to find examples

**Future-Focused**
- What should future you remember?
- What will save time in the next session?

### ❌ DON'T

**Be Vague**
- ❌ "Added some pages"
- ✅ "Added getting-started.md with wiki-links to about.md and example-note.md"

**Skip Failures**
- ❌ Only document what worked
- ✅ Document build failures, broken links, etc.

**Just List Changes**
- ❌ "Modified config"
- ✅ "Updated quartz.config.ts to enable graph view and search"

---

## Retrospective Storage Structure

```
.claude/
├── SESSION-RETROSPECTIVE-TEMPLATE.md  # Template to copy
├── RETROSPECTIVE-PROCESS.md           # This guide
└── retrospectives/
    ├── 2026-01-02-initial-content-setup.md
    └── README.md  # Index of all retrospectives
```

---

## Integration with Documentation

### claude.md
- **Purpose:** Project overview and conventions
- **Updated:** When patterns change or new conventions emerge
- **Content:** How Quartz works, content guidelines, deployment

### .claude/SESSION-SUMMARY.md
- **Purpose:** Running task list and work tracking
- **Updated:** During and at end of session
- **Content:** What's done, what's in progress, what's next

### Retrospectives
- **Purpose:** Learning and pattern documentation
- **Updated:** End of major work or sessions
- **Content:** Why decisions were made, what worked/failed

---

## Benefits

### Immediate
- Clear record of what was done and why
- Patterns documented while fresh
- Next steps defined

### Short-term (Next Session)
- Faster ramp-up time
- Avoid repeating mistakes
- Reuse proven patterns

### Long-term (Weeks/Months Later)
- Content organization strategy documented
- Configuration decisions explained
- Pattern library for digital gardens

---

*This process creates a flywheel where each session's learnings compound into future sessions.*
