# Content Organization

Documents folder structure under `content/`, how slugs are formed, and how paths map to URLs in Quartz.

---

## Folder Structure

```
content/
├── index.md                    # Homepage
├── notes/                      # Evergreen notes
│   ├── concept-one.md
│   ├── concept-two.md
│   └── ...
├── posts/                      # Blog posts
│   ├── 2026-01-02-first-post.md
│   ├── 2026-01-05-second-post.md
│   └── ...
├── projects/                   # Project pages
│   ├── project-alpha.md
│   ├── project-beta.md
│   └── ...
├── profile/                    # Profile page
│   └── index.md
├── about.md                    # Site meta pages
├── getting-started.md
└── example-note.md
```

---

## Path Conventions

### Evergreen Notes

**Pattern:** `content/notes/<slug>.md`

**Slug Rules:**
- Lowercase
- Kebab-case (hyphens, not underscores)
- Descriptive but concise
- No dates in filename

**Examples:**
- `content/notes/zettelkasten-method.md`
- `content/notes/public-learning.md`
- `content/notes/atomic-notes.md`

**URL Mapping:**
- File: `content/notes/zettelkasten-method.md`
- URL: `/notes/zettelkasten-method/`

### Blog Posts

**Pattern:** `content/posts/YYYY-MM-DD-<slug>.md`

**Slug Rules:**
- Must start with ISO date: `YYYY-MM-DD-`
- Followed by kebab-case slug
- Date must match frontmatter `date` field

**Examples:**
- `content/posts/2026-01-02-building-digital-garden.md`
- `content/posts/2026-01-05-learning-rust.md`

**URL Mapping:**
- File: `content/posts/2026-01-02-building-digital-garden.md`
- URL: `/posts/2026-01-02-building-digital-garden/`

### Projects

**Pattern:** `content/projects/<slug>.md`

**Slug Rules:**
- Lowercase
- Kebab-case
- Match project name closely
- No version numbers in slug (use frontmatter)

**Examples:**
- `content/projects/quartzsite.md`
- `content/projects/content-manager-skill.md`

**URL Mapping:**
- File: `content/projects/quartzsite.md`
- URL: `/projects/quartzsite/`

### Profile

**Pattern:** `content/profile/index.md`

**Rules:**
- Exactly one profile page
- Must be named `index.md` inside `profile/` folder
- No alternative profiles

**URL Mapping:**
- File: `content/profile/index.md`
- URL: `/profile/`

---

## Slug Generation

### From Title to Slug

**Algorithm:**
1. Take the title from frontmatter
2. Convert to lowercase
3. Replace spaces with hyphens
4. Remove special characters (keep letters, numbers, hyphens)
5. Remove leading/trailing hyphens
6. Collapse multiple hyphens to single hyphen

**Examples:**

| Title | Slug |
|-------|------|
| "Zettelkasten Method" | `zettelkasten-method` |
| "Building a Second Brain" | `building-a-second-brain` |
| "How I Learn Rust (2026)" | `how-i-learn-rust-2026` |
| "C++ vs Rust: Performance" | `c-vs-rust-performance` |

### Special Cases

**Acronyms:**
- Keep together: `"PKM Systems"` → `pkm-systems`
- Not: `p-k-m-systems`

**Numbers:**
- Keep as-is: `"Web3 Basics"` → `web3-basics`

**Ampersands:**
- Replace with "and": `"Tools & Techniques"` → `tools-and-techniques`

---

## URL Structure

### Quartz URL Mapping

Quartz converts file paths to URLs following these rules:

1. Remove `content/` prefix
2. Remove `.md` extension
3. Add trailing slash
4. `index.md` becomes the folder's URL

**Examples:**

| File Path | URL |
|-----------|-----|
| `content/index.md` | `/` |
| `content/about.md` | `/about/` |
| `content/notes/atomic-notes.md` | `/notes/atomic-notes/` |
| `content/posts/2026-01-02-first-post.md` | `/posts/2026-01-02-first-post/` |
| `content/profile/index.md` | `/profile/` |

### Special Pages

Quartz generates additional pages:

- `/tags/` - All tags index
- `/tags/topic/rust/` - Posts tagged with `topic/rust`
- `/notes/` - Folder listing (if enabled)
- `/posts/` - Folder listing (if enabled)

---

## Organization Principles

### When to Use Folders

**Use folders for:**
- Content types with distinct templates/frontmatter
- Content that benefits from separate listing pages
- Content you want to organize chronologically (posts)

**Don't use deep nesting:**
- ❌ `content/notes/programming/rust/beginner/basics.md`
- ✅ `content/notes/rust-basics.md` + proper tags

### When to Use Tags

**Use tags for:**
- Cross-cutting topics
- Content categorization
- Generating dynamic indexes
- Reader navigation

**Tag hierarchy:**
- Use namespaces: `topic/rust`, `status/active`
- Not deep paths: `programming/rust/basics`

### Balancing Folders and Tags

**Folders** define **structure**:
- Type of content (note vs post vs project)
- Organizational containers

**Tags** define **meaning**:
- What topics content covers
- What state/maturity it has
- How pieces relate

---

## Migration and Reorganization

### Renaming Files

**When you need to rename a file:**

1. ✅ Update all wiki-links pointing to it
2. ✅ Update any explicit path references
3. ✅ Commit with clear message about rename
4. ❌ Don't rename without updating references
5. ❌ Don't change type (e.g., note → post) without frontmatter update

**Example:**
```bash
# Old: content/notes/old-slug.md
# New: content/notes/new-slug.md

# Find all references:
grep -r "old-slug" content/

# Update wiki-links:
# [[old-slug]] → [[new-slug]]
```

### Moving Between Folders

**Only move when:**
- Content type actually changes (rare)
- Fixing misorganization from initial creation

**Process:**
1. Move file to new folder
2. Update frontmatter (especially tags if type changed)
3. Update ALL references
4. Test all links
5. Commit with explanation

### Archiving Content

**Don't delete, archive:**

1. Set `publish: false` in frontmatter
2. Optionally add `archived: true`
3. For projects, set `status: archived`
4. Keep file in place for internal references

---

## Examples

### Well-Organized Structure

```
content/
├── index.md
├── notes/
│   ├── atomic-notes.md
│   ├── digital-garden.md
│   ├── evergreen-notes.md
│   ├── pkm-systems.md
│   └── zettelkasten-method.md
├── posts/
│   ├── 2026-01-02-building-digital-garden.md
│   ├── 2026-01-05-learning-rust.md
│   └── 2026-01-10-atomic-note-taking.md
├── projects/
│   ├── quartzsite.md
│   └── content-manager-skill.md
└── profile/
    └── index.md
```

### Poor Organization (Don't Do This)

```
content/
├── notes/
│   ├── programming/
│   │   ├── rust/
│   │   │   ├── beginner/
│   │   │   │   └── basics.md     # Too deep!
│   ├── my-note-1.md              # Generic name
│   └── temp.md                   # Placeholder name
├── blog-posts/                   # Should be 'posts/'
│   └── my_first_post.md          # Underscores, no date
└── My Profile.md                 # Spaces, wrong location
```

---

## Quick Reference

### Creating New Content

| Type | Path Pattern | Example |
|------|--------------|---------|
| Evergreen | `content/notes/<slug>.md` | `content/notes/rust-ownership.md` |
| Blog Post | `content/posts/YYYY-MM-DD-<slug>.md` | `content/posts/2026-01-02-learning-rust.md` |
| Project | `content/projects/<slug>.md` | `content/projects/my-app.md` |
| Profile | `content/profile/index.md` | `content/profile/index.md` |

### Slug Rules

- ✅ Lowercase
- ✅ Kebab-case
- ✅ Descriptive
- ❌ Spaces
- ❌ Underscores
- ❌ Special chars

---

*Good organization makes content easy to find, easy to link, and easy to maintain.*
