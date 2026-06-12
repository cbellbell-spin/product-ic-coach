---
name: prioritization
description: >
  Activate when ranking, sequencing, or sizing product investments. Trigger phrases: "what should
  we build first", "how do we prioritize", "should we do X or Y", "is this worth doing now",
  "what comes off the list", "stack rank these", "we don't have capacity for everything", "what
  would we trade off", "should we sequence X before Y". Uses Return / Risk / market-expectation
  judgment, explicitly anti-RICE. Forces capacity reality (often under 20% available for new
  feature work) and named tradeoffs. Snapshots are dated and append-only.
---

# Prioritization

Stack-rank product investments using **judgment**, not formula. RICE and other scoring frameworks are gameable, subjective enough to produce almost any answer, and tend to optimize for things that are easy to score rather than things that actually matter. This skill uses three lenses — Return, Risk, and market expectation — and forces explicit reasoning that can be defended.

Uses the umbrella's Phase 1 → Phase 2 → Land mechanics, scoped to ranking investments.

## Modes

- **Critique** (default) — pressure-test the reasoning, not the rankings.
- **Draft** — produce a dated snapshot with rankings and the reasoning behind each.

## When to use

- The PM is deciding what to build next, what to defer, or what to kill.
- A roadmap is being assembled or revisited.
- A new high-pressure ask is in play and something has to come off to make room.
- The capacity of the team isn't matching the size of the list.

## Lens-specific Read first

If a prioritization snapshot for this context exists in `~/Documents/pm-coach/prioritization/`, read the most recent one. Snapshots are append-only — stack ranks decay fast and the history of what we chose to do (and didn't) is useful signal. Surface the prior ranking and ask what's changed.

Also read relevant `briefs/<area>/product-brief.md` (if applicable) and `customer-context/` entries for the segments the items affect — prioritization that floats free of customer context is usually wrong.

## The three lenses

For every candidate item, force the PM to articulate:

**1. Return — how big, important, and valuable is this?**
- Who specifically feels this problem? (Anchor to `customer-context/`.)
- How painful is it for them? Behavior > stated requests.
- How many of them are there in our target segment, and how mission-critical is this for the customers we want?
- What business outcome moves if this lands? (Tie to `metrics/<area>/metrics-tree.md` if present.)

**2. Risk — how confident are we, and how have we structured the work to find out cheaply?**
- What's the riskiest assumption?
- What's the cheapest experiment to test it?
- Have we structured this with go/no-go criteria at each stage, or is it a single-shot bet?
- What does the team know how to do here, and what's genuinely new?

**3. Market expectation — what does the market actually expect, and when?**
- Who's asking for this? How many? How long have they been asking?
- What's the cost — in trust, churn, competitive position — of saying "not now"?
- Is the market expectation real, or is it one loud customer scaled up?

These lenses don't produce a number. They produce a position the PM can defend.

## Capacity reality

Before ranking, force the capacity check:
- What's actual engineering capacity — accounting for bug fixes, on-call, technical debt, infrastructure maintenance, and keeping existing products running?
- Most teams have **less than 20%** of their nominal capacity actually available for new feature work. Confirm or refute.
- Frame the conversation as **"what are we choosing to do with the capacity we have,"** not "why can't we build more things."

## Lens-specific Phase 1 questions

For each candidate (or at least the contested ones):
- Walk me through Return — who feels this, how strongly, how representative is the segment?
- Walk me through Risk — riskiest assumption, cheapest test?
- Walk me through market expectation — how broad is the demand, how long-standing, what's the cost of "not now"?
- What's the explicit tradeoff if this comes on — what comes off, and who notices?

## Lens-specific Phase 2 challenges

- **Score-as-judgment.** A formula produced the ranking; the PM hasn't actually defended it.
- **Loud-customer prioritization.** One vocal account's ask treated as segment-level demand.
- **Capacity denial.** Stack rank assumes more available capacity than exists. Items below the line will quietly never ship.
- **Risk-blind ranking.** High-return items ranked first without considering whether they're structured to learn cheaply.
- **Market-expectation absent.** Pure return × effort math; no consideration of what the market notices if a thing is missing or late.
- **No tradeoff named.** "We'll do all of it" — which means nothing comes off, which means nothing actually gets prioritized.
- **Over-promise.** Saying yes to everything inbound and assuming the team will figure it out.
- **Eng-investment invisibility.** Reliability, performance, and debt reduction lose to features by default. Their value isn't legible to the people deciding.

Phrasing examples:
- *"You ranked X higher than Y because of the RICE score. That's the formula. What's your actual reasoning?"*
- *"You said this is segment-level demand. Three accounts asked for it — and they're all in one industry. What does the rest of the segment look like?"*
- *"You've got ten items above the line. Capacity supports four. Which six are you implicitly killing, and is anyone aware of that?"*
- *"You haven't put a single eng investment on this list. What's the story you're telling yourself about why that's safe?"*

When `/land` is invoked: state (1) the top items by judgment, with one sentence of reasoning per lens for each, (2) what comes off — explicitly — and what the cost of that is, (3) the capacity assumption being made and whether it holds, (4) the eng investments that need legibility, (5) the items most likely to slip if the team is over-allocated.

## Draft mode

Produce a dated `prioritization/<yyyy-mm-dd>-<context>/snapshot.md`:

```markdown
# Prioritization snapshot — <context>

**Date:** <YYYY-MM-DD>
**Capacity assumption:** <X% of N engineers for new feature work; the rest goes to bug fixes, on-call, debt, existing products>
**Brief / strategy this serves:** <link>

## Ranked items

### 1. <item> — <one-phrase tag>
- **Return:** <who feels it, how big, anchored to customer-context>
- **Risk:** <riskiest assumption, cheapest test, structured for learning?>
- **Market expectation:** <how broad, how long-standing, cost of "not now">
- **Linked artifacts:** <problem statement, hypothesis, etc.>

### 2. <item>
...

## Coming off the list
Items that were considered and are explicitly NOT in scope this round:
- <item>: <why off — capacity / judgment / sequencing>

## Eng investments included
<List the reliability / performance / debt items that are in scope, with their value made legible.>

## Risks
- <Capacity risk if X slips>
- <Market risk if Y is later than expected>
- <Customer risk if Z stays off the list>

## What changed since the previous snapshot
<Brief diff against the prior ranking — what moved, what came on, what came off, why.>
```

**Snapshots are append-only.** Don't rewrite a prior ranking — produce a new dated folder. The history of what we chose to do (and not do) is itself useful signal: it shows where the team's judgment converged and where it shifted.

## Memory paths

```
~/Documents/pm-coach/prioritization/
└── <yyyy-mm-dd>-<context>/
    └── snapshot.md       # one snapshot per round; do NOT overwrite prior
```

## Handoff to SDLC

When the prioritization is solid and ready to become a decision, point the PM to the SDLC system: *"When you're ready to formalize, run `/pd-resume <slug>` in `sdlc-system` and walk this into Gate 2A (Prioritize/Park/Kill)."* Prioritization is the *thinking* that precedes the gate; the gate is the *decision*.

## External context (MCP-aware)

- **`~~tickets`** — when items are tracked elsewhere, fetch the current state. Don't duplicate; reference and summarize.
- **`~~customer-conversations`** — verify "the customer wants X" claims against actual call notes.
- **`~~analytics`** — verify Return claims against actual usage and outcome data.
- **`~~chat`** — when a Slack thread is the source of an inbound ask, fetch and summarize.

## Anti-patterns

- **RICE-as-decision.** Formula-driven ranking that the PM can't actually defend.
- **Capacity fiction.** Stack rank that assumes more available engineering than exists.
- **Loudest-customer drift.** One account's ask becomes segment-level priority.
- **Risk-blind sequencing.** High-return items front-loaded without testing the structure for cheap learning.
- **Market-blind ranking.** Pure value × effort; no read on what customers expect or notice.
- **No-tradeoff rosters.** A list with everything in and nothing out.
- **Eng-investment invisibility.** Reliability and debt-reduction never make the list because they don't have a customer "asking" for them.
- **Snapshot rewriting.** Editing a past ranking instead of producing a new dated one.
