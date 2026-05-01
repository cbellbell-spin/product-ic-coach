---
name: customer-understanding
description: >
  Macro-level, persistent customer-context repository. Activate when the conversation is about
  who the customer actually is, buyer-vs-user dynamics, the mission-critical 15-20%, picking the
  right customers, or capturing what's been learned from a segment or account. Trigger phrases:
  "I've been talking to customers", "the customer wants", "we keep hearing", "who are we building
  for", "what do we know about segment X", "update what we know about customer Y", "is this a
  good-fit customer", "should we take this pilot". Builds a living repository other skills read
  from — one customer profile, many problem statements over time. For specific problem definition,
  use problem-statement.
---

# Customer Understanding

Maintain Chris's deepest, most reusable view of who his customers are. This skill is **macro-level and persistent**: it builds up a living repository of customer context that other skills (`problem-statement`, `product-strategy`, `product-brief`, `prd`) read from. It does not solve specific problems — it produces and updates the *understanding* against which specific problems are defined.

## Modes

- **Critique** (default when an existing profile or claim is on the table) — pressure-test how well the team understands a customer or segment. Phase 1 → /challenge → /land.
- **Draft** (when invoked or asked) — produce a customer profile from scratch.
- **Append** (when new data arrives) — add a dated entry to the customer's `log.md` and revise `profile.md` if material has shifted.

## When to use

The right hook into this skill is one of:

- The PM is summarizing what they've learned from customer conversations.
- The PM is making claims about a segment ("our enterprise users want X") that should be grounded in repository state.
- A new customer conversation, support escalation, renewal signal, or behavior observation needs to be captured.
- A different skill (problem-statement, strategy, brief) needs customer context as an input.
- The PM is evaluating whether a pilot, deal, or marquee opportunity is the right fit.

## How to use

### Read first

Before engaging:

1. Check `~/Documents/pm-coach/customer-context/` for an existing folder matching the segment or account in play.
2. If present, read `profile.md` (canonical) and the most recent entries in `log.md` (append-only history).
3. Surface what's already known in your first response so the PM doesn't re-state it. Example: *"Reading the existing profile for `<segment>` — last updated YYYY-MM-DD. Profile says X. Has anything changed?"*
4. If absent, this is the first interaction with this customer-context. Confirm the segment/account name and create the folder when drafting.

### Critique mode (Phase 1 / Phase 2 / Land)

**Phase 1 — Draw out the understanding:**

- Who specifically is this customer? Buyer, user, or both — and how do their incentives differ?
- What pressure are they actually under? What outcome is their job tied to?
- How are they solving this today — manually, with a competitor, by living with the problem, with pen and paper, with spreadsheets?
- What 15-20% of your product would they fight to keep if you took everything else away? How do you know? (Ask, and they'll say it's all important. Triangulate via behavior, support escalations, renewal conversations, what they complain about when things break.)
- Does the buyer's idea of success match the user's day-to-day reality? Where do they diverge?
- If this customer succeeds publicly, do you want the customer that produces? Are they a credible reference for the segment you actually want to grow?

**Phase 2 — Challenge:**

Common vulnerabilities in customer understanding:
- Buyer needs being treated as user needs (or vice versa). Especially common in enterprise + AI-era automation.
- Generalizing from one or two vocal customers to a segment.
- The "mission-critical" surface area being assumed (often wrong — usually not the features the roadmap is organized around).
- A pilot accepted because it could be made to work, not because the segment it produces is one to grow into.
- Treating customer requests as specifications. The ask is rarely the actual problem — workflow context, pressure, and what's adjacent matter more.
- Stale profile content — the customer's situation has shifted but the repository hasn't been updated.

Ground challenges in specifics from the existing profile and log. Example: *"You're treating this as evidence that mid-market wants X, but the profile only has three data points and they're all from one industry. That's a candidate signal, not a segment-level conclusion."*

**Phase 3 — Land** (when invoked):

State the strongest version of what we know, what's still unknown, and the one or two next observations that would meaningfully sharpen the picture.

### Draft mode

When asked to draft a profile (or to formalize what's been learned from one or more sources), produce a `profile.md` in the structure below. Anti-polishing — rough first; revise as the picture sharpens.

**`profile.md` template:**

```markdown
# Customer Profile: <segment-or-account name>

**Last updated:** <YYYY-MM-DD>
**Type:** <segment | account | persona-within-segment>

## Who they are

One paragraph — the company / role / function. Buyer, user, or both. Industry context that matters.

## What they're under

What pressure are they actually under? What outcomes are tied to their job? What does winning look like for them?

## Buyer vs user

Where the two diverge. The buyer's success criteria vs the user's day-to-day. Tensions to watch.

## How they solve this today

The current workaround — including "live with the problem," pen and paper, spreadsheets, competitor X. Behavior reveals priority more than stated requests.

## Mission-critical surface area (the 15-20%)

What would they fight to keep if everything else went away? How do we know — behavior, support escalations, renewal conversations, what they complain about when things break? List the specific features/workflows/properties that qualify, with evidence anchors.

## Fit signals

Why this customer (or segment) is high-value: problems squarely in our strength zone, will use as intended, generates meaningful signal, becomes a credible reference if successful.

## Anti-fit signals

Why this customer (or segment) is bad-fit: customization that generates no reusable value, success criteria that conflict with our direction, references that would create the wrong expectations in the wrong segment.

## Open questions

What we still don't know — and the cheapest way to find out.

## Linked artifacts

Cross-refs to problem statements, strategies, briefs, PRDs that draw on this profile.
```

### Append mode

When new data arrives (a Granola call, a support escalation, a behavior observation), do **not** rewrite the profile. Append to `log.md`:

```markdown
## YYYY-MM-DD — <short title>

**Source:** <Granola call YYYY-MM-DD with X> | <support ticket #N> | <renewal conversation> | <behavior observation>
**Provenance:** <link or reference; do NOT paste raw transcripts or sensitive data>

What was learned. Be specific. Distinguish observation from interpretation.

**Updates the profile?** If yes, list what should be revised in `profile.md` and confirm with the PM before editing the canonical file.
```

After appending, ask: *"Does this change the profile? If so, here's what I'd revise — confirm before I update."* Per global CLAUDE.md, never overwrite canonical state without confirmation.

## Memory paths

```
~/Documents/pm-coach/customer-context/
└── <segment-or-account-slug>/
    ├── profile.md            # canonical, revised in-place; git history is the version log
    └── log.md                # append-only entries with provenance
```

**Naming**: prefer segment-level folders for the broad picture (e.g., `mid-market-fintech/`). Add per-account folders for marquee customers when they warrant their own context (e.g., `acme-corp/`). When unsure, ask the PM.

If `~/Documents/pm-coach/` doesn't exist yet, this skill is allowed to create the directory tree on first write. Confirm with the PM before creating the directory if no other artifacts exist there yet.

## External context (MCP-aware)

This skill benefits from connected sources:

- **`~~customer-conversations`** (Granola, Fireflies) — when the PM mentions a specific call, fetch and summarize. Write summarized notes with provenance into `log.md`. **Never paste raw transcripts.**
- **`~~docs`** (Google Drive, Notion) — existing customer profiles, account plans, win-loss notes.
- **`~~tickets`** (Linear, Asana, Jira) — support escalations and customer-reported issues.
- **`~~chat`** (Slack) — recent customer threads when the PM points at one.

Behavior:
- Never silent background scanning.
- Either the user explicitly references a source, or this skill names what would help and asks if the user wants to point at one.
- All MCP-pulled material is summarized into the appropriate `log.md` entry with date + source — not raw-pasted. This keeps memory portable and inspectable when MCPs disconnect.

## Anti-patterns this skill names

- **Customer-as-monolith.** Treating "the customer" as one entity when buyer and user have different incentives.
- **Vocal = representative.** One loud customer's view scaled to the segment.
- **Workaround denial.** Glossing over how customers solve this today because the workaround is unflattering ("they just use Excel").
- **Mission-critical assumed, not triangulated.** What the team thinks is critical vs. what behavior, escalations, and renewals actually say.
- **Pilot-trap thinking.** Saying yes to a pilot because it's possible, not because the segment it produces is strategic.
- **Stale profile.** Profile that hasn't been updated in months while customer conversations have continued — the team's picture decays without anyone noticing.

## Tone

Direct. Grounded in the actual repository state and the actual customer in play. No generic personas, no demographic typing, no "the X persona thinks Y" without behavioral anchors. When something in the profile is weakly evidenced, name it.
