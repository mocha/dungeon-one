# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Dungeon One — Agent Instructions

This is a TTRPG world-building and campaign management vault (not a software project — there are no build, test, or lint commands). It uses plain Obsidian markdown with YAML frontmatter and wiki-links to build a knowledge graph of a fictional world.

## Vault Structure

```
dungeon-one/
├── world/              # Persistent lore bible (exists across campaigns)
│   ├── characters/     # PCs, NPCs, villains
│   ├── locations/      # Places at any scale (continents to closets)
│   ├── factions/       # Organizations, guilds, groups
│   ├── creatures/      # Monsters and beasts
│   ├── items/          # Weapons, artifacts, potions, trinkets
│   ├── lore/           # History, legends, culture, magic systems, custom rules
│   └── deities/        # Gods and cosmic forces
├── campaigns/          # Campaign-specific content
│   └── [campaign-name]/
│       ├── sessions/   # Session logs
│       ├── quests/     # Storylines and objectives
│       └── notes/      # Prep, brainstorming, ideas
└── _templates/         # Obsidian templates (blank forms)
```

### Navigation
Each directory contains an `llms.txt` file with a brief overview of what's there and a listing of current contents. **Read these for orientation before creating or searching for content.** After creating new entity files, update the relevant `llms.txt` to include them.

### Boilerplates
Each entity directory has a `_boilerplate.md` showing a complete example entry with HTML comments guiding what goes in each section. Use these as reference for tone, structure, and linking style.

### World vs. Campaigns
The `world/` directory holds everything that exists in the fictional world — it persists across campaigns. The `campaigns/` directory holds campaign-specific content: session logs, quests, and planning notes. Multiple campaigns can share the same world.

### Creating a New Campaign
Copy `campaigns/_campaign-boilerplate/` to `campaigns/[campaign-name]/`, rename it, and update its `llms.txt`. The boilerplate includes stub directories for sessions, quests, and notes.

## Entity Schemas

Every entity is a markdown file with YAML frontmatter. The body is descriptive prose organized under `## Description`, `## Background`, and `## Notes` headings (though these can vary).

### Character (`world/characters/`)
```yaml
type: character
role: pc | npc | villain       # What role they play in the story
name:                          # Display name
player:                        # Real person playing this character (blank = NPC)
race:
class:
location: "[[Current Location]]"
factions: ["[[Faction Name]]"]
status: alive | dead | missing | unknown
tags: []
```

### Location (`world/locations/`)
```yaml
type: location
name:
parent: "[[Parent Location]]"           # What this is inside of
connections: ["[[Adjacent Location]]"]   # What you can reach from here
ruler: "[[Character]]"
factions: ["[[Faction]]"]
tags: []
```
Locations are flat files — hierarchy comes from the `parent` field, not folder nesting. A room's parent is a building, a building's parent is a district, a district's parent is a city, and so on.

### Faction (`world/factions/`)
```yaml
type: faction
name:
alignment:
headquarters: "[[Location]]"
leader: "[[Character]]"
tags: []
```

### Creature (`world/creatures/`)
```yaml
type: creature
name:
creature_type:
size:
habitat: ["[[Location]]"]
tags: []
```

### Item (`world/items/`)
```yaml
type: item
name:
category: weapon | armor | potion | artifact | wondrous | mundane
rarity: common | uncommon | rare | very-rare | legendary | artifact
owner: "[[Character]]"
location: "[[Location]]"
tags: []
```

### Lore (`world/lore/`)
```yaml
type: lore
name:
category: history | legend | prophecy | culture | magic | religion | custom
related_locations: ["[[Location]]"]
related_characters: ["[[Character]]"]
tags: []
```

### Deity (`world/deities/`)
```yaml
type: deity
name:
domains: []
alignment:
followers: ["[[Faction]]"]
tags: []
```

### Session (`campaigns/[name]/sessions/`)
```yaml
type: session
campaign: "[[Campaign Name]]"
session_number:
date_played: YYYY-MM-DD
locations: ["[[Location]]"]
npcs: ["[[Character]]"]
tags: []
```

### Quest (`campaigns/[name]/quests/`)
```yaml
type: quest
campaign: "[[Campaign Name]]"
status: active | completed | failed | abandoned
quest_giver: "[[Character]]"
locations: ["[[Location]]"]
tags: []
```

## Conventions

### File Naming
- Entity files are named after the entity: `Maren Ashveil.md`, `Thornhaven.md`, `The Verdant Circle.md`
- Session files use the pattern: `Session NNN - Title.md` (e.g., `Session 001 - The Road to Thornhaven.md`)
- Quest files are named after the quest: `Find the Lost Grove.md`

### Linking Rules
- **Always use wiki-links** for relationships between entities: `"[[Name]]"` in frontmatter, `[[Name]]` in body text
- **Frontmatter links must be quoted**: `location: "[[Thornhaven]]"` not `location: [[Thornhaven]]`
- **List fields use arrays**: `factions: ["[[The Verdant Circle]]", "[[The Iron Compact]]"]`
- **Dangling links are intentional** — reference entities before they exist. The link graph pre-connects things.
- **Inline links in prose** — when mentioning a character, location, faction, or any other entity in the body text, link it: `She works for [[The Verdant Circle]] in [[Thornhaven]]`

### Content Style
- Write descriptive prose, not stat blocks or data tables
- Write for a DM who will read this aloud or reference it mid-session
- First person is fine for session notes; third person for world entries
- Be vivid but concise — a paragraph of description is better than a page of stats

### What NOT to Do
- **Don't invent lore that contradicts existing entries** — read the world before generating. If a faction's page says their leader is Kael, don't create an NPC who's described as their leader unless it's Kael.
- **Don't create files outside established directories** — if something doesn't fit the existing entity types, put it in `lore/`
- **Don't use Obsidian plugins or Dataview syntax** — everything must work as plain markdown
- **Don't use HTML** — except for comments in boilerplate files
- **Don't add frontmatter fields that aren't in the schema** — if extra metadata is needed, put it in the body text under `## Notes`

### Generating Content
When asked to create new world content:
1. **Read existing world entries first** — check what already exists in the relevant directories and related directories
2. **Maintain consistency** — new content should feel like it belongs in this world. Reference existing characters, locations, and factions where appropriate.
3. **Use the templates** — output files must match the frontmatter schema exactly
4. **Link generously** — every reference to an existing entity should be a wiki-link
5. **Create stubs for new references** — if your new entry mentions an entity that doesn't exist yet, consider creating a minimal stub for it

### Tags
Tags are freeform and user-defined. No enforced taxonomy. Common patterns:
- Role tags: `merchant`, `quest-giver`, `antagonist`, `ally`
- Descriptive tags: `undead`, `magical`, `cursed`, `ancient`
- Campaign tags: `arc-1`, `side-quest`, `main-plot`
