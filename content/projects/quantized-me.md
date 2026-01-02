---
title: "Quantized.me"
description: "Obsidian-based knowledge system with dual-pane MOCs, circular backlinking, AI integration, and custom plugins—shipped as a product."
tags:
  - type/project
  - topic/obsidian
  - topic/pkm
  - topic/ai
status: "active"
draft: false
publish: true
---

# Quantized.me

An Obsidian-based knowledge management vault designed as a **[[vault-as-product|product]]**, not just a personal note collection. Combines custom plugins, AI integration via MCP, and a modular architecture for knowledge capture, organization, and intelligence.

## Overview

**Core System:**
- Obsidian vault with custom JavaScript modules
- Companion capture app (screen/video capture + web scraping)
- AI-aware architecture with embedded Claude skills
- Drop-in module system for extensibility

**Target Users:**
- Knowledge workers building second brains
- Developers managing code + notes together
- Content creators tracking ideas and sources
- Teams needing shared knowledge systems

## Status: Active

**Current Phase:** Development and dog-fooding
- Building core modules (Kanban, dual-pane MOCs)
- Testing circular backlinking system
- Developing AI integration patterns
- Preparing for beta release

**Next Milestones:**
- MVP: Dual-pane MOCs + custom plugins functional
- Beta: Waitlist onboarding + community forum
- V1: Full drop-in module system

## Key Features

### 1. Circular Backlinking

**Core Rule:** If item A affects item B in any way, they are linked together.

**Implementations:**
- **Prompts Library**: Prompts ↔ chats that use them
- **Scripts Tracker**: Scripts ↔ files created by those scripts
- **Active Notes Tracker**: Logs every note visited during navigation

This creates a self-aware system where relationships are explicit and navigable.

### 2. Dual-Pane MOCs (Maps of Content)

Enhanced data visualization for browsing vault content across multiple dimensions:

**Browse By:**
- Reddit threads
- YouTube videos
- Browser history
- Vault taxonomy
- Business ideas
- Daily notes
- Coding projects
- Available MCP servers
- AI chat library

Each MOC shows filterable properties and supports drill-down exploration.

### 3. AI Chat Library

Semantic connection between vault notes and AI chat properties:

- Venn diagram concept: **AI chats ∩ Vault** = navigable through MOC
- MOC shows filterable properties from chats
- Links chat conversations to vault content based on topics

### 4. QM Tax (Quantized.me Taxonomy)

Corpus of vault information used to embed new content correctly:

**Process:**
1. AI gathers vault structure/context
2. Detects content type → applies `content_type` property
3. References QM tax → formulates substantive field values
4. Embeds content with correct frontmatter

**Content Types:**
- Prompts, Artifacts, Templates, Tools
- Video, Image, Audio notes
- Scripts, Plugins, Configs

### 5. Custom Plugins

**Collection Browser Plugin:**
- Dual-pane interface for vault exploration
- Multi-context support (Search, Prompts, Templates, Tools)
- Property-based filtering + content registry navigation
- Subtypes for specialized view modes

**Activity Watch Integration:**
- Vault + Browser + Computer tracking
- Growth visualization over time
- Timeline of vault evolution

### 6. Capture Ecosystem

**Screen/Video Capture:**
- Overlay with text/image annotation
- Direct send to vault
- Providence/source attribution

**Web Scraping:**
- Like Obsidian WebClipper
- Captures content → markdown notes
- Maintains source links

**Audio Notes:**
- Voice memo → AI transcription → 2 clicks to vault

## Tech Stack

**Platform:**
- Obsidian (base)
- TypeScript for plugins
- JavaScript modules (drop-in components)
- Python & PowerShell scripts

**AI Integration:**
- Claude via MCP (Model Context Protocol)
- `.claude/skills/obsidian-plugin-architect/` - Plugin development patterns
- Vault intelligence skill for querying structure

**Data Layer:**
- Frontmatter schemas
- Tag taxonomies
- Content registry (JSON)

## Development Philosophy

### Axioms

- **Tinker system**: It's Obsidian, things change, AI can help
- **Intuitive and modular**: Easy to understand and extend
- **Self-aware**: System knows its own settings, plugins, experiences
- **Solve friction when you see it**: Avoid context switching
- **Reusable modules**: Easy to transpose to different situations

### Drop-In Module Pattern

Each feature ships as a **downloadable folder/note** that works immediately:

```
/modules/
  /dual-pane-moc/
    - Plugin files
    - Documentation
    - Example content
    - Configuration
```

This makes the vault extensible without breaking existing functionality.

## Monetization Strategy

### Conversion Percentage Model

- Free vault demonstrates when paying for AI is valuable
- Points users to standard vs advanced (paid) AI options
- User uses discount code → creator gets conversion percentage

### Direct Sales

- Modules sold individually
- Full vault sold as configured product
- Subscription for updates

### Partnership Approach

- "Junk food software": 3-4 questions → module configured for specific need
- Low-friction onboarding
- Waitlist → formatted note → embeds into vault → leads to forum

## Technical Highlights

### Frontmatter Strategy

**Assignment Levels:**
1. **Automatic**: `date_created`, `date_modified`
2. **Per content type**: Recognizable property keys
3. **AI or manual**: Additional categorization

**Special Fields:**
- `content_type` - What kind of item this is
- `when_to_use` - Usage context
- `chat_link` - URL to related AI chat

### Desired Integrations

- **Copilot**: Access models with vault context
- **Shared Cloud Folder**: Multiple AI chats on same project
- **Language Toggle**: Flip switch to change entire vault language
- **Community Collab**: Backlink stats on prompt/tool performance
- **Timeline**: Vault activity visualization over time

## Related Notes

Concepts that inform this project:

- [[vault-as-product]] - Core philosophy of shipping configured systems
- [[claude-skills-pattern]] - How AI understands the vault structure
- [[circular-backlinking]] - Relationship tracking pattern
- [[content-governance-via-code]] - Frontmatter and quality enforcement
- [[documentation-as-architecture]] - Self-documenting vault design

## Related Posts

Development journey:

- [[2026-01-02-ai-native-documentation]] - How AI integration patterns emerged
- *(More posts to come as development progresses)*

## Links

- **Repository**: *(To be released)*
- **Documentation**: Embedded in vault
- **Community**: *(Forum/Discord to be launched)*

---

**Status updated: 2026-01-02**
**Current focus:** Building core module system and testing with real usage
