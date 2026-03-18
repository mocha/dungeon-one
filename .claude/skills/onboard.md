---
name: onboard
description: First-time setup for a new world. Walks the user through establishing their world's basics and importing existing lore from descriptions, documents, or conversation. Triggers on "onboard", "set up my world", "get started", "import my campaign", "first time setup", or when working with an empty world directory.
---

# Onboard

Walk a new user through setting up their world in Dungeon One.

## Process

1. **Welcome and orient**:
   - Briefly explain the vault structure (world vs. campaigns, entity types)
   - Explain the three ways to create content (boilerplate, template, conversation)
   - Keep it warm and brief — don't overwhelm

2. **Ask about their world**:
   Start broad and narrow down. Ask one question at a time:
   - "Tell me about your world. What's the big picture?" (setting, tone, genre, scale)
   - "What's the most important place?" (start with the hub — where the campaign begins)
   - "Who are the key players?" (major NPCs, factions, powers)
   - "Is there a campaign in progress, or is this a new world?"

   Let the user talk freely. Extract structure from their descriptions rather than asking them to fill forms.

3. **If importing from existing notes**:
   - Ask if they have existing documents (Google Docs, text files, notes) they want to bring in
   - If they paste or describe existing lore, parse it into the entity model:
     - Identify characters, locations, factions, items, creatures, lore
     - Group them and present: "I found 5 characters, 3 locations, and 2 factions in what you've shared. Want me to create entries for all of them?"
   - Generate entries that preserve the user's original language and ideas — don't over-edit their voice

4. **Create the foundational entries**:
   - Start with the top-level location(s) (the world, continent, or starting region)
   - Then the starting settlement or hub location
   - Then key NPCs and factions
   - Then any active campaign setup

   Create in relationship order so entries can reference each other.

5. **Set up the first campaign** (if applicable):
   - Copy `campaigns/_campaign-boilerplate/` to `campaigns/[campaign-name]/`
   - Fill in the campaign's `llms.txt` with the premise and party
   - Create PC entries if the user describes their players' characters

6. **Wrap up**:
   - Show them what was created (summary list with entry counts)
   - Explain next steps: "You can browse these in Obsidian, edit anything, and add more whenever you want. Try opening the graph view to see how everything connects."
   - Remind them about templates and boilerplates for self-service creation

## Key Rules
- Meet the user where they are. If they have a detailed world, focus on structured import. If they're starting fresh, help them brainstorm.
- Preserve the user's voice. When they describe something, use their words in the entries. Don't genericize their creative vision.
- Don't generate what they haven't described. Fill in structure, not content. If they mention a city but don't describe it, create a stub, not a fully detailed entry.
- Keep the first session manageable. 10-20 entries is a good starting batch. More can come later.
- Make it feel like progress, not homework. Every entry created is their world taking shape.
