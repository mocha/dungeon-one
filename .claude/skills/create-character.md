---
name: create-character
description: Create a new character (PC or NPC) for the world. Use when the user wants to add a person to their world — a tavern keeper, a villain, a player character, a mysterious stranger. Triggers on "create a character", "new NPC", "I need a character", "make me a villain", or any request to add a person to the world.
---

# Create Character

Create a new character entry in `world/characters/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/characters/llms.txt` for orientation
   - Read `CLAUDE.md` for the character schema and conventions
   - Scan existing characters in `world/characters/` to understand the world's tone, naming conventions, and existing relationships
   - If the user mentions a location or faction, read those entries too

2. **Gather information** from the user. Ask conversationally — don't present a form. Key things to learn:
   - Who is this character? (name, race, class/occupation)
   - What's their role? (pc, npc, villain)
   - If a PC, who's playing them?
   - Where are they? (location — check existing locations)
   - Are they affiliated with any existing factions?
   - What's their deal? (personality, appearance, background — even a sentence is enough)

   If the user already provided most of this in their request, don't re-ask. Fill in what you have and only ask about what's missing or unclear. A character can start minimal and be fleshed out later.

3. **Generate the character file**:
   - File name: `world/characters/{Character Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Write vivid, concise prose — a paragraph for Description, a paragraph or two for Background, bullet points for Notes
   - **Link generously** — every mention of an existing location, faction, or character should be a `[[wiki-link]]`
   - Include plot hooks, secrets, or personality quirks in the Notes section — these are gold for a DM

4. **Consider stub creation**: If the character references locations or factions that don't exist yet, mention them to the user. Offer to create stubs but don't do it automatically.

5. **Update llms.txt**: Add the new character to `world/characters/llms.txt` under the Contents section.

## Output Format

Use the Write tool to create the file. The file must match this structure:

```markdown
---
type: character
role: [pc|npc|villain]
name: [Full Name]
player: [blank for NPCs]
race: [race]
class: [class or occupation]
location: "[[Current Location]]"
factions: ["[[Faction]]"]
status: alive
tags: []
---

# [Full Name]

## Description
[Physical appearance, mannerisms, first impressions — 2-4 sentences]

## Background
[Origin, motivation, history — 1-3 paragraphs, as much as needed]

## Notes
[Bullet points: secrets, plot hooks, personality quirks, voice notes, DM reminders]
```

## Key Rules
- Read the world before writing. Consistency matters.
- Don't invent lore that contradicts existing entries.
- If the user gives you a vague request ("I need a shopkeeper"), lean into the existing world to make the character feel like they belong.
- Less is more. A vivid paragraph beats a page of generic detail.
