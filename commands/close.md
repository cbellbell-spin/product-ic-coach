---
description: Session deposit — reflector pass over the conversation, propose decisions.md entries, ask if brief.md needs updating.
---

## /close

Session-end ritual. Applies Mann's session deposit question: *"What does this problem know now that it didn't know at the start?"*

Run this before ending any coaching session on a named problem. Can be user-invoked or suggested by the umbrella at natural session-end signals (see Suggestion Behavior below).

### Behavior

1. **Identify the active slug.** Use the problem opened with `/open`, or infer it from the conversation if clear. If ambiguous, ask: "Which problem should I log this against?"

2. **Reflector pass.** Scan the full conversation for:
   - **Settled calls** — positions the PM committed to, conclusions reached, framings accepted
   - **Rejected calls** — things tried and explicitly abandoned, with the reason
   - **Open items** — questions explicitly left unresolved, evidence gaps named, things deferred
   - **Phase 2 outcomes** — if a challenge was run, what survived it; what didn't

   Do not log exploratory thinking that went nowhere without a conclusion. Log decisions, not process.

3. **Propose `decisions.md` entries.** Format as a dated block. Present all proposed entries at once for review — do not write yet:

   ```
   Here's what I'd log from this session:

   ## YYYY-MM-DD
   - **Settled:** [X] — [brief reason]
   - **Rejected:** [Y] — [brief reason]
   - **Open:** [Z] — [what would resolve it]
   ```

   If nothing decision-worthy happened (exploratory session, stuck in Phase 1), say so directly: "Nothing decision-worthy to log — this was an exploratory session. That's fine, but it might mean the brief needs sharpening."

4. **Wait for confirmation or edits.** The PM may correct, remove, or add entries. Once confirmed, append the approved block to `~/Documents/pm-coach/problems/<slug>/decisions.md`.

5. **Ask about brief.md.** One question: "Does the brief need updating — did the scope or working hypothesis shift?" If yes, propose specific edits to `brief.md` and confirm before writing. If no, close without touching it.

6. **Confirm close.** One line: "Logged. Session closed for [slug]."

### What not to log

- Exploratory questions that didn't land anywhere
- Phase 1 Socratic back-and-forth before a position emerged
- Summaries of what was discussed (that's what `sessions/<date>.md` is for)
- Anything the PM explicitly says not to log

### Suggestion Behavior (umbrella-triggered)

The umbrella skill should suggest `/close` — one quiet line at the end of a response — when any of these signals appear:

- The PM says something like "I think I'm good for now", "that's helpful, thanks", "I'll take it from here"
- `/land` was just invoked and a synthesis was produced
- `/solid` was just invoked signaling the PM is confident and done
- `/reset` is about to be invoked on a named problem (suggest closing before clearing)
- The session has been running long (substantive exchanges on a named problem, clear arc of Phase 1 → Phase 2 → Land completed)

Suggestion format (one line, like all command suggestions):

> *"Ready to log this? `/close` will capture what was settled before you go."*

Do not suggest `/close` if:
- No named problem slug is in play (umbrella-only conversation with no `/open` called)
- The session was very short or clearly exploratory with nothing to log
- `/quiet` is active
