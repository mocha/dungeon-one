---
name: create-item
description: Create a new item for the world. Use when the user wants to add a weapon, artifact, potion, magic item, or notable mundane object. Triggers on "create an item", "new weapon", "I need a magic item", "make a potion", or any request to add an object to the world.
---

# Create Item

Create a new item entry in `world/items/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/items/llms.txt` for orientation
   - Read `CLAUDE.md` for the item schema and conventions
   - If the item has an owner or is in a specific location, read those entries
   - Check lore entries for magic systems or crafting traditions that would influence the item's nature

2. **Gather information** from the user:
   - What is this item? (name, general nature)
   - What does it do? (properties, magical effects)
   - Where is it? Who has it?
   - How rare/powerful is it?
   - Where did it come from? (crafted, ancient, cursed, found)

   For vague requests ("I need loot for a dungeon"), read the dungeon/location context and generate something fitting.

3. **Generate the item file**:
   - File name: `world/items/{Item Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Description should make the item feel tangible and distinctive
   - Properties can be as mechanical or narrative as the user wants
   - Notes should include provenance, plot hooks, and complications

4. **Update llms.txt**: Add the new item to `world/items/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: item
name: [Item Name]
category: [weapon|armor|potion|artifact|wondrous|mundane]
rarity: [common|uncommon|rare|very-rare|legendary|artifact]
owner: "[[Character]]"
location: "[[Location]]"
tags: []
---

# [Item Name]

## Description
[What does it look like? What's it made of? How does it feel? 2-4 sentences.]

## Properties
[What does it do? Mechanical effects, narrative powers, or both. As specific or vague as needed.]

## Notes
[Bullet points: origin story, who wants it, curses, complications, plot hooks.]
```

## Key Rules
- Items should feel like they belong in this world. Connect them to existing lore, factions, or history.
- A good item has a story. Even a simple healing potion is more interesting if you know who made it and why.
- Don't over-specify mechanics unless the user asks. Narrative properties ("cuts through magical barriers") are more versatile than stat blocks.
