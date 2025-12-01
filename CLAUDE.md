# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Fantasia is a D&D 5e campaign setting inspired by western pop music, published as a digital garden using Quartz v4. The primary purpose of this repository is to document the campaign world, characters, locations, and lore.

## Build Commands

### Development Server
```bash
npx quartz build --serve
```
Starts local server at `http://localhost:8080/` with hot-reloading for content changes.

### Production Build
```bash
npx quartz build
```
Builds static site to `public/` directory.

### Type Checking & Testing
```bash
npm run check    # TypeScript + Prettier check
npm run format   # Format all files
npm test         # Run tests with tsx
```

## Content Structure

All campaign content lives in `content/` as Markdown files:

### Campaign Setting Theme

This is a **music-themed D&D universe** where:
- The world was created through music (see the founding myth in `World/Cosmology.md`)
- Major forces/factions are organized by musical sections: **Percussion** (drums of war, orcs), **Strings** (order and diplomacy, Piano Man's domain), **Wind** (change and transformation)
- Planes include an **Orchestral plane** that appears as a giant orchestra hall
- Magic items have music themes: Knife of Transposition, Dress of Love, instrument panel
- Key mechanic: **Transposition** - interplanar travel where time passes differently between planes (2x factor)

## Writing Content

### Wikilinks

Use **wikilinks** extensively to connect content:

```markdown
[[Page Name]]                    # Links to Page Name.md with text "Page Name"
[[Page Name|Display Text]]       # Links with custom display text
[[Page Name#Section]]            # Links to specific section
[[World/Forces#Percussion]]      # Links to section in another folder
![[Image.png]]                   # Embeds image
![[Page]]                        # Transcludes entire page
```

Wikilinks are resolved using the "shortest path" algorithm - if there are multiple files with the same name, the shortest path is preferred. Links can be written without full paths if unambiguous.

### Frontmatter

Use YAML frontmatter for metadata:

```markdown
---
title: Page Title
tags:
  - location
  - faction
draft: false
---
```

Common fields:
- `title`: Page title (defaults to filename if omitted)
- `tags`: List of tags for organization
- `draft`: Set to `true` to hide from published site
- `description`: For link previews
- `aliases`: Alternative names for this page

### Callouts

Use Obsidian-style callouts for special content:

```markdown
> [!info]
> This is informational content shared with players.
```

### Content Organization Patterns

- **World-building** goes in `content/World/`
- **NPCs** go into `content/NPC/`.
- **PCs** go into `content/PC/`.
- **Songs** go into `content/Song`.
- **Index/home page** is `content/index.md` (campaign summary and current state)
- Use folders to group related content
- Pages should be noun-focused (places, people, things, concepts)
- Avoid creating pages for common words; use descriptive multi-word titles

## Ignored Patterns

The following patterns in `content/` are ignored (see `quartz.config.ts`):
- `private/` folder
- `templates/` folder
- `.obsidian/` folder

## Quartz Configuration

Key settings in `quartz.config.ts`:
- **Link resolution**: Uses `"shortest"` path algorithm - files can be linked by name alone if unambiguous
- **Custom OG Images**: `Plugin.CustomOgImages()` is enabled but can be commented out to speed up build times during development
- **Analytics**: GoatCounter analytics configured for site tracking
- **Deployment**: Site deployed to `fantasia.zeroindexed.com`

## Markdown Features

Supported syntax:
- **GitHub Flavored Markdown**: footnotes, strikethrough, tables, task lists
- **Obsidian Flavored Markdown**: callouts, wikilinks, tags
- **LaTeX**: Math expressions with `$inline$` or `$$block$$` (KaTeX rendering)
- **Syntax highlighting**: Code blocks with language tags
- **Mermaid diagrams**: Not currently enabled in config but available
