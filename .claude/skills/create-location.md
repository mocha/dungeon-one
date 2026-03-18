---
name: create-location
description: Create a new location in the world. Use when the user wants to add a place — a city, a dungeon, a tavern, a mountain range, a room in a castle. Triggers on "create a location", "new place", "I need a town", "add a dungeon", or any request to add a place to the world.
---

# Create Location

Create a new location entry in `world/locations/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/locations/llms.txt` for orientation
   - Read `CLAUDE.md` for the location schema and conventions
   - Scan existing locations in `world/locations/` to understand the world's geography and naming patterns
   - If the user mentions a parent location, read that entry to understand what already exists there

2. **Gather information** from the user. Ask conversationally:
   - What is this place? (name, general nature)
   - What is it inside of? (parent location — a building is in a city, a city is in a region)
   - What's nearby or connected? (roads, neighboring areas, portals)
   - Who controls it? (ruler, dominant faction)
   - What's it like? (mood, appearance, notable features)

   If the user provided enough in their request, don't re-ask. Infer the parent from context if obvious (e.g., "a tavern in Thornhaven" → parent is Thornhaven).

3. **Generate the location file**:
   - File name: `world/locations/{Location Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Write for a DM who needs to describe this place to players on the spot
   - **Link generously** — connect to parent location, neighboring locations, characters who live here, factions that operate here
   - Include sensory details (what you see, hear, smell) in Description
   - Include DM-useful details in Notes (secrets, encounters, what happens here)

4. **Update related entries**: If this location has a parent, mention to the user that the parent's entry might want a reference to this new child location. Offer to update it.

5. **Update llms.txt**: Add the new location to `world/locations/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: location
name: [Location Name]
parent: "[[Parent Location]]"
connections: ["[[Adjacent Place]]"]
ruler: "[[Character]]"
factions: ["[[Faction]]"]
tags: []
---

# [Location Name]

## Description
[What does this place look like? Sensory details. First impressions. 2-5 sentences.]

## Details
[What's notable? Who's here? What happens here? History? 1-3 paragraphs.]

## Notes
[Bullet points: secrets, encounter ideas, plot hooks, things the party might find or interact with.]
```

## Key Rules
- Hierarchy is everything. Always set the `parent` field. A location without a parent is a top-level region or world.
- `connections` describe adjacency and travel — what you can reach FROM here. Parent/child is containment.
- Read existing locations to maintain geographic consistency.
- Sensory writing matters — DMs read location descriptions aloud.
