---
name: create-faction
description: Create a new faction or organization for the world. Use when the user wants to add a group — a guild, cult, army, noble house, thieves' network, merchant company, or any organized group. Triggers on "create a faction", "new guild", "I need an organization", "add a group", or any request to add an organization.
---

# Create Faction

Create a new faction entry in `world/factions/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/factions/llms.txt` for orientation
   - Read `CLAUDE.md` for the faction schema and conventions
   - Scan existing factions in `world/factions/` and characters in `world/characters/` to understand the political landscape
   - If the user mentions a location or leader, read those entries

2. **Gather information** from the user:
   - What is this group called?
   - What do they want? (goals, ideology)
   - Who leads them?
   - Where are they based?
   - What's their alignment/disposition? (helpful, sinister, neutral, chaotic)

   Keep it conversational. If the user gives a brief request, generate something that fits the existing world and offer to refine.

3. **Generate the faction file**:
   - File name: `world/factions/{Faction Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Write Goals & Methods as actionable DM content — what would this faction DO if the party crossed them? Helped them?
   - **Link to existing entries** — leader, headquarters, rival factions, member characters
   - Notes should include internal politics, secrets, and plot hooks

4. **Consider related updates**: Mention to the user if existing characters should have this faction added to their `factions` field. Offer to update them.

5. **Update llms.txt**: Add the new faction to `world/factions/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: faction
name: [Faction Name]
alignment: [alignment or disposition]
headquarters: "[[Location]]"
leader: "[[Character]]"
tags: []
---

# [Faction Name]

## Description
[What is this group? What do outsiders know? 2-4 sentences.]

## Goals & Methods
[What do they want? How do they operate? What are they willing to do? 1-3 paragraphs.]

## Notes
[Bullet points: internal politics, secrets, plot hooks, relationships with other factions, what happens if the party gets involved.]
```

## Key Rules
- Factions are the engines of conflict. Write them with opposing goals to other factions.
- Members are tracked on character entries (characters list factions in their `factions` field), not on the faction page.
- If a faction has a leader who doesn't exist yet, offer to create them.
