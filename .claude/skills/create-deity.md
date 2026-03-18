---
name: create-deity
description: Create a new deity, god, spirit, or cosmic force for the world. Triggers on "create a deity", "new god", "I need a deity", "add a god", or any request to add a divine or cosmic power to the world.
---

# Create Deity

Create a new deity entry in `world/deities/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/deities/llms.txt` for orientation
   - Read `CLAUDE.md` for the deity schema and conventions
   - Scan existing deities and lore entries to understand the world's theological landscape
   - Check factions — some may be religious orders

2. **Gather information** from the user:
   - What is this deity's name and nature?
   - What do they govern? (domains — war, nature, trickery, death, etc.)
   - What's their disposition? (alignment, personality)
   - Who worships them? (existing factions, cultures, races)
   - How do they manifest? (how they're depicted, how they interact with mortals)

3. **Generate the deity file**:
   - File name: `world/deities/{Deity Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Description should convey how the deity is perceived — art, visions, myths
   - Tenets & Worship should give a DM enough to roleplay a follower
   - Notes should include theological conflicts, lost temples, divine politics, plot hooks

4. **Update llms.txt**: Add the new deity to `world/deities/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: deity
name: [Deity Name]
domains: [list of domains]
alignment: [alignment]
followers: ["[[Faction]]"]
tags: []
---

# [Deity Name]

## Description
[How is this deity perceived? What do they look like in art, visions, myth? 2-4 sentences.]

## Tenets & Worship
[What do followers believe? How do they worship? What are the rules? 1-3 paragraphs.]

## Notes
[Bullet points: theological disputes, rivalries with other gods, lost temples, divine artifacts, plot hooks.]
```

## Key Rules
- Deities should create story potential. Rivalries between gods, disputed doctrines, fallen temples — these are DM gold.
- Connect deities to existing factions and locations where possible.
- Leave room for mystery. Mortals may not fully understand their gods.
