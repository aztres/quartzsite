---
title: "Getting Started with Quartz"
tags:
  - guide
  - quartz
---

# Getting Started with Quartz

This is a quick guide to working with your Quartz digital garden.

## Creating New Notes

1. Create a new `.md` file in the `content/` folder
2. Add frontmatter with a title:
   ```yaml
   ---
   title: "Your Note Title"
   tags:
     - tag1
     - tag2
   ---
   ```
3. Write your content in Markdown

## Linking Between Notes

Use wiki-style links to connect your notes:

- `[[other-note]]` - Links to other-note.md
- `[[other-note|Custom Text]]` - Link with custom text
- `[[folder/note]]` - Link to notes in subfolders

Example: Check out the [[about|About page]] to learn more.

## Organizing Content

### Tags
Add tags to your frontmatter to categorize content:
```yaml
tags:
  - programming
  - web-development
```

### Folders
Create subfolders in `content/` to organize by topic:
- `content/notes/` - General notes
- `content/projects/` - Project documentation
- `content/guides/` - How-to guides

## Markdown Features

Quartz supports standard Markdown plus some extensions:

- **Bold** and *italic* text
- Lists and checklists
- Code blocks with syntax highlighting
- Tables
- Images
- Callouts and admonitions

## Publishing Changes

After creating or editing content:

```bash
git add content/
git commit -m "Add new content"
git push origin v4
```

GitHub Actions will automatically rebuild and deploy your site.

## Next Steps

- Explore the [[about|About page]]
- Start creating your own notes
- Customize the site configuration in `quartz.config.ts`

---

[[index|← Back to Home]]
