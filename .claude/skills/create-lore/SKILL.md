---
name: create-lore
description: Create a new lore entry for the world — history, legends, prophecies, cultural practices, magic systems, or custom rules. Use when the user wants to document something about how the world works. Triggers on "create lore", "add history", "write a legend", "describe the magic system", "how does X work in this world", or any worldbuilding that isn't a character, place, faction, creature, or item.
---

# Create Lore

Create a new lore entry in `world/lore/`.

## Process

1. **Read existing world context** before generating anything:
   - Read `world/llms.txt` and `world/lore/llms.txt` for orientation
   - Read `CLAUDE.md` for the lore schema and conventions
   - Scan existing lore entries to understand established worldbuilding — don't contradict it
   - Read related character, location, and faction entries if the lore connects to them

2. **Gather information** from the user:
   - What is this lore about? (event, tradition, magic system, cultural practice)
   - What category does it fit? (history, legend, prophecy, culture, magic, religion, custom)
   - How does it connect to existing world elements?
   - Is this established fact in the world, or something that might be myth/disputed?

   For broad requests ("tell me about the history of this region"), read what exists and generate lore that enriches and connects existing entries.

3. **Generate the lore file**:
   - File name: `world/lore/{Lore Entry Name}.md`
   - Use the exact frontmatter schema from CLAUDE.md
   - Summary should be a quick-reference overview (2-3 sentences)
   - Details can be as long as the topic warrants
   - **Link extensively** — lore entries are the connective tissue of the world
   - Notes should include consequences, open questions, and things the party might discover

4. **Update llms.txt**: Add the new entry to `world/lore/llms.txt` under the Contents section.

## Output Format

```markdown
---
type: lore
name: [Lore Entry Name]
category: [history|legend|prophecy|culture|magic|religion|custom]
related_locations: ["[[Location]]"]
related_characters: ["[[Character]]"]
tags: []
---

# [Lore Entry Name]

## Summary
[Quick-reference overview — what is this? 2-3 sentences.]

## Details
[The full account. As much or as little as the world needs. Link to related entries.]

## Notes
[Bullet points: consequences still felt today, open mysteries, things the party could discover, disputed versions of this history.]
```

## Key Rules
- Lore is the connective tissue. It should reference and enrich existing entries, not exist in isolation.
- Leave mysteries open. "No one knows why the grove shattered" is better than explaining everything.
- Write lore that creates plot hooks. History that doesn't affect the present isn't useful to a DM.
