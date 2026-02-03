# byterover-openclaw
An explanation of why ByteRover's memory solution is a powerful replacement for Openclaw's memory implementation

# A Better Memory Architecture

---

## Two-Tier System: ByteRover + Daily Logs

### 🧠 ByteRover - Long-Term Knowledge Base
*What it is:* Semantic knowledge graph managed via CLI (⁠ brv ⁠ commands)

*What goes here:*
- People & relationships (contacts, family, work network)
- Preferences & patterns (communication style, dining preferences, work habits)
- Important decisions & context
- Repeatable workflows & procedures
- Location-specific knowledge

*How it works:*
```bash
# Query (retrieval)
brv query "Who is Eddie Thai?" --headless --format json
→ Semantic search across context tree
→ Returns: "Eddie Thai, business partner, +xxxxxxxxx, recurring meetings"

# Curate (storage)
brv curate "New preference or decision" --headless --format json
→ AI organizes into context tree structure
→ Automatic topic categorization (no manual filing)

# Sync to cloud
brv push --headless --format json -y
→ Backed up at https://app.byterover.dev/team/space
```

*When I use it:*
- ⁠Before answering questions about people, preferences, or past decisions
- ⁠When user mentions something worth remembering long-term
- ⁠During heartbeats to distill daily logs into reusable knowledge

*Security:* Only queried in main session (direct chats with user), never in group chats or shared contexts


### 📝 Daily Logs - Raw Activity Tracking
*What it is:* Chronological markdown files (⁠ memory/YYYY-MM-DD.md ⁠)

*What goes here:*
- ⁠Conversations & events from that day
- Work completed & tasks closed
- ⁠Temporary notes & context
- System changes & troubleshooting
- Anything worth remembering but not yet "knowledge"

*How it works:*
- Write throughout the day as things happen
- Keep recent days (today + yesterday) for immediate context
- Review periodically and extract patterns → curate to ByteRover
- Archive older logs once knowledge is extracted

*Retention:* Recent days stay active, older ones get archived after knowledge curation



### 📋 Supporting Files

*TASKS.md*
- ⁠Active work tracker (urgent, in-progress, completed)
- ⁠Reviewed every heartbeat
- ⁠Source of truth for "what needs doing now"

*CAPABILITY-LOG.md*
- ⁠System configuration changes
- ⁠Tool installations & integrations
- Capability expansions

*heartbeat-state.json*
- ⁠Tracks last check timestamps (email, calendar, calls)
- ⁠Prevents redundant checks
- ⁠Enables smart scheduling

---

## Why This Architecture is Better

### Before (MEMORY.md only):
- ⁠*Flat file* - everything in one place, hard to navigate
- *Manual search* - grep/ctrl-f to find anything
- *No structure* - "where does this go?" decisions every time
- ⁠*Duplication* - same info written multiple times in different contexts
- ⁠*No retrieval intelligence* - exact keyword matches only
- ⁠*Growth problem* - file gets huge, slow, overwhelming

### After (ByteRover + Daily Logs):

*1. Scalable Knowledge Management*
- Context tree grows intelligently
- ⁠AI organizes knowledge by topic automatically
- ⁠No manual filing decisions

*2. Semantic Retrieval*
- ⁠Query natural language: "What restaurants does Binh like?"
- ⁠Returns synthesized answer from multiple sources
- ⁠Works even if exact keywords weren't used

*3. File-Aware Context*
⁠- Can curate with ⁠ --files ⁠ to link knowledge to actual scripts/configs
- ⁠Example: ⁠ brv curate "Email workflow" --files check-binh-calendar.sh ⁠

*4. No Knowledge Duplication*
- ByteRover merges related context automatically
- One canonical place for each piece of knowledge

*5. Query-First Mindset*
- ⁠Forces me to check before acting ("retrieve then respond")
- ⁠Prevents forgetting or contradicting past context

*6. Separation of Concerns*
- ⁠Raw logs (daily .md) vs curated knowledge (ByteRover)
- ⁠Temporary context vs permanent wisdom
- ⁠Activity tracking vs decision database

*7. Cloud Sync & Portability*
- Knowledge backed up automatically
- ⁠Viewable online at https://app.byterover.dev/team/space
- ⁠Could be accessed from multiple systems if needed

*8. Better Compaction*
- Daily logs can be compacted/archived without losing knowledge
- ⁠ByteRover persists the important stuff
- ⁠Workspace stays lean

---

## Workflow Example

*User mentions:* "Eddie handles finances, meets weekly"

*I do:*
1.⁠ ⁠*Curate to ByteRover:*
```bash
   brv curate "Eddie Thai handles finances, weekly business meetings with Binh" --headless --format json
    ⁠
   → ByteRover adds to ⁠ structure/work_network/eddie_thai.md ⁠, merges with existing Eddie context
```
2.⁠ ⁠*Log to daily file:*
```bash
   ## 13:45 - Eddie's Role
   User clarified Eddie handles finances, weekly meetings
   Curated to ByteRover.
```
⁠
*Later, user asks:* "Who handles finance?"

*I do:*
1.⁠ ⁠*Query ByteRover:*
```bash
   brv query "Who handles finances?" --headless --format json
    ⁠
   → Returns: "Eddie Thai handles finances, business partner, weekly meetings"
```

2.⁠ ⁠*Respond with confidence* - retrieved from curated knowledge, not guessing

---

## Why Not Just Use Daily Logs?

*Daily logs are:*
- Chronological (great for "what happened when")
- ⁠Unsorted (you have to read through to find things)
- ⁠Temporary (meant to be reviewed and distilled)
- ⁠Context-rich but noisy

*ByteRover is:*
- ⁠Topical (great for "what do I know about X")
- ⁠Indexed (semantic search finds it instantly)
- ⁠Permanent (the distilled essence)
- ⁠Signal not noise

*Both are needed:*
- ⁠Logs capture the raw stream of consciousness
- ⁠ByteRover captures the wisdom extracted from that stream
- ⁠Together they provide continuity without overwhelming future sessions

---

## Security Model

*ByteRover queries are only allowed in main session:*
- Direct WhatsApp chats with Binh ✅
- Group chats ❌
- Discord ❌
- ⁠Sessions with other people ❌

This prevents accidentally leaking personal context (contacts, preferences, private decisions) in shared/public contexts.

Daily logs have the same restriction - only loaded in main session.

---

## Result

A memory system that:
- ⁠*Scales* as knowledge grows
- ⁠*Retrieves* semantically, not just keyword matching
- *Organizes* automatically, no manual filing
- ⁠*Persists* across sessions and compactions
- ⁠*Separates* raw logs from curated knowledge
- *Protects* private context from shared spaces

It's the difference between having a pile of notebooks vs a searchable, organized knowledge base that gets smarter over time.
