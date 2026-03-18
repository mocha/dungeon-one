---
name: create-creature
description: Create a new creature or monster for the world. Use when the user wants to add a beast, monster, or other non-character being. Triggers on "create a creature", "new monster", "I need a beast", "what creatures live here", or any request to add wildlife or monsters.
---

# Create Creature

Create a new creature entry in `world/creatures/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/creatures/llms.txt` for orientation
   - Read `CLAUDE.md` for the creature schema and conventions
   - If the user mentions a habitat or location, read those entries to understand the environment
   - Scan existing lore for any magic systems or worldbuilding that would influence what creatures exist

2. **Gather information** from the user:
   - What kind of creature? (or let the agent generate something fitting)
   - Where does it live?
   - How dangerous is it?
   - Any special traits or behaviors?

   For vague requests ("what lives in the forest?"), read the relevant location entries and generate something that fits the environment and tone of the world.

3. **Generate the creature file**:
   - File name: `world/creatures/{Creature Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Description should be vivid enough to read aloud during an encounter
   - Behavior section should help a DM run this creature — how it fights, what it does when threatened, whether it can be reasoned with
   - Notes should include encounter hooks, loot, and connections to the wider world

4. **Update llms.txt**: Add the new creature to `world/creatures/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: creature
name: [Creature Name]
creature_type: [type]
size: [size]
habitat: ["[[Location]]"]
tags: []
---

# [Creature Name]

## Description
[What does it look like? What's distinctive? 2-4 sentences of vivid, encounter-ready description.]

## Behavior
[How does it act? Hunt? React to threats? Can it be tamed? Is it intelligent? 1-2 paragraphs.]

## Notes
[Bullet points: encounter ideas, loot/materials, lore connections, what the locals say about it.]
```

## Key Rules
- Write for encounter use. A DM should be able to read the Description section aloud when the party first sees this creature.
- Tie creatures to the world — habitat links, connections to local lore, reasons they exist in this setting.
- Don't write mechanical stat blocks. Describe capabilities in narrative terms.
