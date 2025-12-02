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
tags:
  - orc (or elf, human, dwarf, etc)
aliases:
  - Some name
  - Another name
---
```

Common fields:
- `tags`: List of tags for organization
- `aliases`: Alternative names for this page

### Callouts

Use Obsidian-style callouts for special content:

```markdown
> [!info]
> This is informational content shared with players.
```

### Content Organization Patterns

- **Concepts** (cosmology, forces, cycles) go in `content/Concept/`
- **Events** (major campaign events) go in `content/Event/`
- **Items** (magical items, artifacts) go in `content/Item/`
- **Locations** (cities, buildings, landmarks) go in `content/Location/`
- **NPCs** go into `content/NPC/`
- **PCs** go into `content/PC/`
- **Songs** go into `content/Song/`
- **Index/home page** is `content/index.md` (campaign summary and current state)
- Use folders to group related content
- Pages should be noun-focused (places, people, things, concepts)
- Avoid creating pages for common words; use descriptive multi-word titles

## Writing Style Guide

### Chronology and Timeline Sections

**Use "## Chronology" for:**
- NPC files
- Location files
- Item files

**Use "## Timeline" for:**
- Event files only

**Subsection formatting:**
```markdown
## Chronology

### Major Event Name

- Bullet point narrative
- Another detail
- Outcome

### Next Event

- More narrative
```

**Key principles:**
- Use `###` headers for major subsections (not bold text)
- Event names should be descriptive (e.g., "### The Ball Massacre" not "### Session 12")
- Organize chronologically within the section

### Timeline References

**Use event anchors instead of technical notation:**

Good:
- "During [[Material Plane Riots]]"
- "After [[The Intervals]]"
- "Two full moons before [[Material Plane Riots]]"

Avoid:
- "T+0" or "T+2 weeks"
- Session numbers as primary organization (these are DM-specific)
- Vague temporal references without event links

**Link to Event pages** to provide temporal context and enable cross-referencing.

### Section Ordering

**For NPC files:**
1. Frontmatter (tags, aliases)
2. Brief intro paragraph (1-2 sentences)
3. `## Description` - Physical appearance, role, key traits
5. `## Chronology` - Events in order
6. `## Connections` - Related NPCs, locations, items

**For Location files:**
1. Frontmatter
2. Brief intro paragraph
3. `## Description` - Geographic context, features, atmosphere
5. `## Chronology` - What happened here
7. `## Connections` - Links to other locations, travel routes

**For Item files:**
1. Frontmatter
2. Brief intro paragraph
3. `## Description` - What it is, basic appearance
4. `## Mechanics` - How it works (can use bold for labels like "**Activation:**")
5. `## Chronology` - Discovery, use, history
6. `## Connections` - Related characters, locations, events

**For Event files:**
1. Frontmatter
2. Brief intro paragraph summarizing the event
3. `## Timeline` - When things happened
4. `## Events` - What happened (with ### subsections)
5. `## Aftermath` - Consequences and outcomes
6. `## Connections` - Related events, people, places

### Bold Text Usage

**Use bold text for:**
- Inline labels in technical descriptions: `**Function:** Creates portals`
- Emphasis within narrative: `**critically important detail**`
- Labels in lists: `**Material Plane:** baseline time flow`

**Do NOT use bold text for:**
- Section headers (use `###` instead)
- Event names in chronology (use `###` instead)
- Replacing proper header hierarchy

### Narrative Voice and Tense

**Past tense for completed events:**
- "Party rescued children from burning orphanage"
- "Maurice revealed his connection to The Binding"
- "Queen hosted a ball to establish peace"

**Present tense for current state:**
- "Piano Man's reign is crumbling"
- "City shows signs of decay"
- "The Dress of Love is a magical garment"

**Third person perspective:**
- Write from neutral narrator viewpoint
- Avoid first person ("we discovered") unless in quoted text
- Keep focus on campaign events and characters

### Wikilink Patterns

**Always link:**
- First mention of major NPCs, locations, items in each section
- Key events that provide temporal context
- Related concepts (Forces, Planes, etc.)

**Use aliases for alternate names:**
```markdown
[[Piano Man|Man of Strings]]
[[Maurice|The Gambler]]
[[Princess of Diamonds|Bonnie]]
```

**Section references for specific content:**
```markdown
[[Forces#Percussion|drums of war]]
[[Material Plane Riots#The Trial]]
```

**Song references:**
- Link songs directly using wikilinks: `[[Africa]]`, `[[Piano Man]]`
- Do NOT use quotes around song links: ~~`"[[Africa]]"`~~ ❌
- Use quotes only for non-linked song titles or lyrics

### Frontmatter Standards

**Required fields:**
```yaml
---
tags:
  - primary-category
  - specific-tags
---
```

**Optional but recommended:**
```yaml
---
title: Display Title (if different from filename)
tags:
  - category
aliases:
  - Alternate Name
  - Another Alias
description: Brief description for link previews
---
```

**Common tag patterns:**
- Locations: `location`, `city`, `material-plane` or `feywild`
- NPCs: race, class
- Items: related concepts, e.g. `transposition`
- Events: location, plane
- PCs: race, class

### Tag Usage Guidelines

**Keep tags minimal and meaningful:**
- Use 2-4 tags per page maximum
- Tags should aid navigation and discovery, not describe every attribute
- Prefer specific, unique tags over generic ones

**Common patterns:**
- NPCs: race (if relevant to story), class (if defined)
- Locations: `location`, plane designation (`material-plane`, `feywild`, etc.)
- Items: primary concept or mechanic (`transposition`, `artifact`)
- Events: primary location or plane where event occurred
- PCs: race, class

**Avoid:**
- Over-tagging with every attribute (don't tag "strong", "magic", "important", etc.)
- Duplicate information already in filename or content
- Tags that would apply to most pages

### Callout Usage

Use callouts sparingly for:
- Information shared with players (use `> [!info]`)
- Meta-information or trivia (use `> [!INFO] Trivia`)
- Out-of-character notes about rules or mechanics

**Do not use callouts for:**
- Standard narrative content
- Chronology sections
- Regular descriptions

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
