---
description: Open a problem by slug and load its brief + decisions into context. Collapses Phase 1 warm-up by surfacing what's already settled.
---

## /open [slug]

Session-start ritual for a problem that has prior history. Loads the Mann artifact structure for the slug and orients the PM before doing anything else.

### Behavior

1. **Resolve the slug.** If the PM provides one (e.g., `/open retention-workflow-q3`), use it directly. If they reference a problem by name without a slug, check `INDEX.md` to find the matching slug. If ambiguous, show the closest matches and ask.

2. **Read `brief.md`.** Located at `problems/<slug>/brief.md`. This is the coaching spec — what we're trying to figure out, current working hypothesis, constraints, open questions. If it doesn't exist, create a stub (see Scaffold below) and prompt the PM to fill it.

3. **Read `decisions.md`.** Located at `problems/<slug>/decisions.md`. Scan for what's settled, what's been rejected and why, and what's explicitly marked open. If it doesn't exist, create an empty one.

4. **Surface state in 3–4 sentences.** Synthesize the two files into a brief, specific orientation — not a recitation. Lead with where things broke off; name what's live and what's settled. Example:

   > "We're working on the retention-workflow problem for mid-market ops leads. The customer persona is settled — it's the ops lead, not the SMB founder. The retention framing was rejected (evidence was 2 edge-case accounts, not representative). Live question: is this workflow friction or a change-management problem? Evidence audit from last session was inconclusive — you flagged needing behavioral data."

5. **Ask one question.** "Where do you want to pick up?" Do not begin Phase 1 or Phase 2 until the PM responds.

### Scaffold — if brief.md doesn't exist

Create `problems/<slug>/brief.md` with this template and ask the PM to fill it now or confirm they'll fill it later:

```markdown
# Brief: <slug>

## What we're trying to figure out
<!-- The core coaching question for this problem. 1–3 sentences. -->

## Current working hypothesis
<!-- What we think is true right now. This will change. -->

## Key constraints
<!-- Time, resources, dependencies, non-negotiables. -->

## Open questions (as of <date>)
<!-- The 2–3 things blocking a clear position. -->
```

Also create an empty `problems/<slug>/decisions.md` with header:

```markdown
# Decisions Log: <slug>

<!-- Append-only. Format each entry as:
## YYYY-MM-DD
- **Settled:** [what was concluded and why]
- **Rejected:** [what was tried and why it was abandoned]
- **Open:** [what remains unresolved]
-->
```

### Notes

- If the slug's `problem-statement.md` already exists, note it briefly: "The problem statement for this one exists — want to reference it or are we still upstream of that?"
- Do not re-read these files mid-session unless the PM explicitly asks. Load once at open, then work from that context.
- If `/open` is invoked mid-session (after already working), treat it as a context refresh: re-read both files, re-surface state, and ask whether to continue where we were or pivot to the loaded context.
