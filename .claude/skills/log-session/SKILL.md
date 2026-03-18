---
name: log-session
description: Log a completed game session. Use after the DM has finished a session and wants to record what happened. Produces a structured session log and can update world state (character locations, quest progress, NPC status). Triggers on "log session", "session recap", "what happened this session", "record session", or any post-game documentation request.
---

# Log Session

Create a session log in the active campaign's `sessions/` directory and optionally update world state.

## Process

1. **Identify the campaign**:
   - Read `campaigns/llms.txt` to find active campaigns
   - If there's only one campaign, use it. If multiple, ask which one.
   - Read the campaign's `llms.txt` and `sessions/llms.txt` to get the session count and recent history

2. **Gather the session narrative** from the user:
   - Ask the user to describe what happened. They can be as brief or detailed as they want.
   - Ask conversationally — "What happened this session?" is enough to start.
   - Follow up on specifics as needed:
     - Where did the action take place?
     - Which NPCs were involved?
     - What major decisions did the party make?
     - Did any quests advance, complete, or fail?
     - Did anything change in the world? (character deaths, location changes, new alliances)

3. **Generate the session file**:
   - Determine the next session number from existing files
   - File name: `campaigns/[campaign]/sessions/Session NNN - [Title].md`
   - Write the Recap as a narrative summary — readable, engaging, captures the feel of the session
   - Key Events as bullet points for quick reference
   - Notes for follow-ups and prep reminders

4. **Offer world state updates**: Based on what happened, identify changes that should propagate:
   - Characters who moved → update their `location` field
   - Characters who died → update their `status` field
   - Quests that advanced → update the quest's Progress section
   - New NPCs encountered → offer to create character entries
   - New locations discovered → offer to create location entries

   **Always ask before making these changes.** Present them as a list: "Based on this session, I'd suggest updating: [list]. Want me to make these changes?"

5. **Update llms.txt**: Add the new session to the campaign's `sessions/llms.txt`.

## Output Format

```markdown
---
type: session
campaign: "[[Campaign Name]]"
session_number: [N]
date_played: [YYYY-MM-DD]
locations: ["[[Location]]", ...]
npcs: ["[[Character]]", ...]
tags: []
---

# Session NNN — [Evocative Title]

## Recap
[Narrative summary of what happened. 2-5 paragraphs. Written in past tense, third person. Should be engaging enough to read as a story recap.]

## Key Events
[Bullet points of important decisions, discoveries, combat outcomes, and plot developments.]

## Notes
[Bullet points: things to follow up on, player decisions that will have consequences, prep notes for next session, loose threads.]
```

## Key Rules
- The recap should be readable as a standalone narrative. Someone who missed the session should understand what happened.
- Link every character, location, and faction mentioned.
- The world state updates are the critical value-add — this is what keeps the vault as a living, stateful representation of the campaign.
- Don't update world state without asking. The DM is the authority.
