---
title: "Vault as Product"
description: "Shipping preconfigured Obsidian vaults as products, not just collections of notes—complete with content, plugins, and AI assistance."
tags:
  - type/evergreen
  - topic/obsidian
  - topic/pkm
  - topic/product
maturity: "sprout"
draft: false
publish: true
---

# Vault as Product

Vault as Product is the concept of treating an Obsidian vault not as a personal note collection, but as a shippable product—a complete knowledge system with content, configuration, custom plugins, and embedded AI assistance.

## Core Shift

**From:** "Here are my notes (copy what you want)"
**To:** "Here's a working knowledge system (drop it in and it works)"

## What Makes a Vault a Product?

### 1. Preconfigured System

Not just markdown files, but:
- **Installed plugins** (community + custom)
- **Configured settings** (hotkeys, workspaces, themes)
- **Working workflows** (templates, scripts, automation)
- **Data structures** (frontmatter schemas, tag taxonomies)

### 2. Embedded Intelligence

The vault includes [[documentation-as-architecture|architectural documentation]] that makes it AI-aware:

- **`claude.md`** - Explains the vault's purpose, structure, and build pipeline
- **`.claude/skills/`** - Enforces frontmatter, tagging, and linking patterns
- **Retrospectives** - Capture how the vault evolved over time

Buyers don't just get notes—they get an AI assistant that already "speaks" the vault's ontology.

### 3. Custom Plugins

Instead of explaining "install these 15 plugins and configure them like this," ship a custom plugin that:
- Implements vault-specific features
- Integrates with the vault's data model
- Provides the unique UX that makes the vault valuable

### 4. Content Included

The vault comes with:
- **Starter content** demonstrating patterns
- **Template library** for common use cases
- **Example workflows** showing how to use it
- **Documentation** embedded in the vault itself

## Example: Quantized.me

The [[quantized-me]] vault ships as a product with:

**Content Layer:**
- Dual-pane MOCs for browsing (Reddit, YouTube, business ideas, etc.)
- Circular backlinking system (if A affects B, they're linked)
- QM Tax (taxonomy for embedding new content correctly)

**Plugin Layer:**
- Custom collection browser plugin
- AI chat library integration
- Activity Watch connector

**AI Layer:**
- `.claude/skills/obsidian-plugin-architect/` - How plugins should be built
- Vault intelligence via MCP
- Skills that understand the vault's structure

**Configuration:**
- Frontmatter schemas
- Tag taxonomies (when_to_use, content_type, etc.)
- Workspace templates
- Style guidelines

Users don't configure this from scratch—they drop in the vault and start working.

## Distribution Pattern: Drop-In Modules

Each feature is a **downloadable folder/note** that drops into an existing vault and works:

```
/modules/
  /dual-pane-moc/
    - Plugin files
    - Documentation
    - Example content
    - Configuration
```

This makes the vault modular and extensible.

## The .claude/ Layer as Product Feature

Including `.claude/` documentation in the product means:

**For Users:**
- AI assistance understands the vault immediately
- No setup required for AI features
- Consistent behavior across sessions

**For Creators:**
- Self-documenting system
- Easier support (AI can answer questions)
- Embedded upgrade path (skills evolve)

## Monetization Patterns

### Direct Sales
- One-time purchase of configured vault
- Subscription for updates and new modules

### Conversion Percentage
- Free vault + affiliate links to AI services
- Vault demonstrates when paid AI is valuable
- User uses discount code → creator gets percentage

### Template Marketplace
- Sell modules/templates separately
- Base vault free, premium modules paid

### Partnership Model
- "Junk food software" - quick setup wizards
- 3-4 questions → module configured for specific need

## What Makes It Valuable

Users pay for:
1. **Time saved** - Hours of configuration done for them
2. **Working system** - Proven patterns, not experiments
3. **Maintenance** - Updates and improvements over time
4. **Intelligence** - AI that understands the domain
5. **Support** - Community and documentation

## Contrast with Sharing Notes

| Sharing Notes | Vault as Product |
|--------------|------------------|
| "Here's my markdown" | "Here's a system" |
| Copy/paste what you want | Works out of the box |
| No configuration | Fully configured |
| Static snapshot | Living product |
| No AI context | AI-aware |

## Technical Requirements

To ship vaults as products:

1. **Portable structure** - Relative paths, no hardcoded locations
2. **Clean dependencies** - All plugins included or installable
3. **Documentation** - Embedded in the vault itself
4. **Version control** - Track changes, enable updates
5. **Installation script** - Automated setup where needed

## Related Concepts

- [[claude-skills-pattern]] - AI assistance built into the product
- [[documentation-as-architecture]] - Self-documenting systems
- [[obsidian-plugin-development]] - Custom features for vaults
- [[knowledge-system-design]] - Structuring information systems

## Projects

- [[quantized-me]] - Obsidian vault being developed as a product
  - Dual-pane MOCs
  - Circular backlinking
  - AI integration via MCP
  - Custom plugins

## Further Reading

- [[2026-01-02-ai-native-documentation]] - AI-native development patterns
- Social media concept: "Shipping Vaults, Not Just Notes"

---

*A vault-as-product isn't just organized notes. It's a configured system, custom tools, and embedded intelligence.*
