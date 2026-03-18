---
name: prep-session
description: Help prepare for an upcoming game session. Reads current world state, recent sessions, active quests, and helps the DM plan scenes, encounters, and narrative beats. Triggers on "prep session", "plan next session", "help me prepare", "what should happen next", or any pre-game planning request.
---

# Prep Session

Help the DM prepare for their next game session by reading the current state of the world and campaign.

## Process

1. **Load campaign context**:
   - Read `campaigns/llms.txt` to find the active campaign
   - Read the campaign's `llms.txt` for current state
   - Read the last 2-3 session logs to understand recent events
   - Read all active quests
   - Read the campaign's `notes/` directory for any existing prep

2. **Load world context**:
   - Read relevant location entries (where the party is, where they might go)
   - Read relevant character entries (NPCs they're likely to interact with)
   - Read relevant faction entries (groups with active interests in the current situation)
   - Check for lore entries that connect to current events

3. **Present a situation brief** to the DM:
   - Where the party is and what they were doing when last session ended
   - Active quests and their current state
   - Unresolved threads from recent sessions
   - NPC motivations that might drive events (factions don't stand still)
   - Upcoming complications or opportunities based on the world state

4. **Collaborate on session planning**:
   - Ask the DM what they want to focus on
   - Suggest 3-5 possible scenes based on current threads
   - For each scene: who's involved, where it happens, what's at stake, possible outcomes
   - Help develop encounter ideas, NPC dialogue prompts, or environmental descriptions
   - Identify any new content that needs to be created (new locations, NPCs, items)

5. **Create a prep note** if the DM wants to save the plan:
   - File: `campaigns/[campaign]/notes/Session [N+1] Prep.md`
   - Include: scenes to run, NPCs to voice, locations to describe, contingencies

## Key Rules
- This skill is collaborative, not prescriptive. The DM knows their table. Suggest, don't dictate.
- Ground everything in existing world state. The value is connecting threads the DM might not have noticed.
- Think about what NPCs and factions would be doing *independently* of the party. The world moves even when the players aren't looking.
- Flag potential problems: "The party agreed to help both the miners and the druids, but those goals conflict — they'll have to choose soon."
- Don't over-plan. 3-5 scenes with flexible outcomes is better than a rigid script.
