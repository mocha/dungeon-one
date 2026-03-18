# Dungeon One

A framework for building and managing TTRPG worlds in Obsidian, with optional AI-assisted workflows.

## What is this?

Dungeon One helps you organize your campaign world — characters, locations, factions, quests, session logs, and everything else — in a way that's easy to browse, easy to search, and gets richer over time.

It works with plain Obsidian. No plugins required. If you also use Claude Code, there are optional AI skills that can help you generate content, but the framework stands on its own without them.

## Quick Start

1. Open this folder as a vault in Obsidian
2. Pick what you want to create (a character, a location, a faction...)
3. Go to the matching directory under `world/` and copy the `_boilerplate.md` file
4. Rename it and start replacing the example content with your own

That's it. You're building your world.

### Three Ways to Create Content

**Copy a boilerplate** — Every directory has a `_boilerplate.md` file showing what a complete entry looks like. Copy it, rename it, replace the content. Good for getting started and understanding the format.

**Use a template** — Obsidian has a built-in "Insert template" command (look in the command palette or set a hotkey). The `_templates/` folder has blank forms for every entity type. Create a new file, insert the template, fill in the fields. Faster once you're comfortable with the format.

**Ask Claude** — If you're using Claude Code, you can describe what you want conversationally and let the AI create properly formatted entries. "I need a grizzled dwarven blacksmith who lives in Irondeep and secretly works for the Shadow Guild." Claude reads your existing world to keep things consistent.

All three produce the same result: a markdown file with frontmatter metadata and descriptive content. Mix and match however you like.

## How the Vault is Organized

```
dungeon-one/
├── world/              # Your persistent lore bible
│   ├── characters/     # PCs, NPCs, villains — everyone
│   ├── locations/      # Places — from continents to closets
│   ├── factions/       # Organizations, guilds, cults, armies
│   ├── creatures/      # Monsters, beasts, and beings
│   ├── items/          # Weapons, artifacts, potions, trinkets
│   ├── lore/           # History, legends, magic systems, culture
│   └── deities/        # Gods, powers, and cosmic forces
│
├── campaigns/          # Stories told in the world
│   └── [your-campaign]/
│       ├── sessions/   # What happened at the table
│       ├── quests/     # Storylines and objectives
│       └── notes/      # Prep, brainstorming, ideas
│
└── _templates/         # Blank forms for Obsidian's template system
```

**World vs. Campaigns** — The world is everything that exists: people, places, history, gods. It persists across campaigns. Campaigns are specific stories happening in that world — they have sessions, quests, and planning notes. You can run multiple campaigns in the same world.

## How Linking Works

This is the most powerful feature and the reason Obsidian works so well for this.

Every entry links to other entries using `[[wiki-links]]`. A character's frontmatter says where they live (`location: "[[Thornhaven]]"`), what factions they belong to (`factions: ["[[The Verdant Circle]]"]`), and the text of their description links to other characters, places, and events.

These links create a **knowledge graph** — a web of connections between everything in your world. Open Obsidian's graph view and you'll see your world as a network. Clusters of connected nodes are communities, trade routes, political alliances. The graph *is* your world map.

**Dangling links are fine.** If you write `[[The Shadow Guild]]` before you've created a page for The Shadow Guild, that's okay. The link will show up in purple, and when you eventually create that page, it'll connect automatically. This means you can reference things before you've fully described them — just like you do when you're worldbuilding in your head.

## Entity Reference

### Characters
Everyone in your world — players, NPCs, villains. The `player` field is what distinguishes PCs from NPCs: if someone is playing this character, put their name there. If it's blank, it's an NPC. Key relationships: where they are (`location`), who they're affiliated with (`factions`), whether they're `alive`, `dead`, `missing`, or `unknown`.

### Locations
Every place, at every scale. A continent, a city, a tavern, a secret room behind the bookshelf. Locations don't need to be organized into folders by size — instead, each location says what it's inside of (`parent: "[[The City]]"`) and what's nearby (`connections: ["[[The Road North]]"]`). This builds your map through relationships, not folder nesting.

### Factions
Organizations, guilds, cults, armies, noble houses, thieves' networks — any group with shared goals. Links to their leader, headquarters, and members (via character entries that list the faction in their `factions` field).

### Creatures
Monsters, beasts, and beings that populate your world. Where they live (`habitat`), what kind of thing they are (`creature_type`), and whatever descriptive detail you want.

### Items
Weapons, armor, potions, artifacts, trinkets, quest items. Who has it (`owner`), where it is (`location`), how rare it is, and what it does.

### Lore
The catch-all for worldbuilding that doesn't fit elsewhere. History, legends, prophecies, cultural practices, magic systems, custom rules. If it's something that's *true about your world* but isn't a person, place, thing, or group — it's lore.

### Deities
Gods, spirits, cosmic forces, patron saints. What they govern (`domains`), their disposition (`alignment`), and who worships them (`followers`).

### Sessions (campaign-specific)
What happened at the table. Numbered, dated, linked to the locations visited, NPCs encountered, and quests advanced. This is your campaign's running history.

### Quests (campaign-specific)
Storylines and objectives. Who gave the quest, where it leads, and whether it's `active`, `completed`, `failed`, or `abandoned`.

## Tips

- **Don't worry about filling every field.** A character with just a name and a one-line description is a valid entry. You can always come back and add more.
- **Dangling links are intentional.** Reference things before they exist. The links will connect when you create those pages later.
- **Tags are optional and freeform.** Use them however you want: `#merchant`, `#quest-giver`, `#antagonist`, `#undead`. There's no enforced taxonomy.
- **The graph view is your friend.** Open it regularly. It shows you the shape of your world and reveals connections you might not have noticed.
- **Start small.** You don't need to describe every corner of your world on day one. Create what you need for the next session, and the world will grow naturally.
