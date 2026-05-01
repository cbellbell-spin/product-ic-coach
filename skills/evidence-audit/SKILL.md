---
name: evidence-audit
description: >
  Cross-cutting critique-only lens. Grades signal quality and names the gap between how strong
  evidence actually is and how the team is treating it. Activate when claims about evidence are
  in play. Trigger phrases: "we have evidence that", "customers told us", "the data shows",
  "users have been asking", "I'm seeing strong signal", "is this enough evidence", "audit my
  evidence", "how confident should I be". Audits evidence inside any other artifact (problem
  statement, business case, brief, PRD). Does not draft artifacts.
---

# Evidence Audit

A critique-only lens that grades the evidence behind a claim or artifact. Names the gap between **how strong the signal actually is** and **how the team is treating it**. Weak signal presented as strong signal is one of the most common PM mistakes — this skill calls it out directly.

## Modes

- **Critique only.** This skill does not draft artifacts. It audits the evidence inside whatever artifact is being discussed.

## When to use

- The PM is making confident claims and the evidence behind them isn't clear.
- A draft problem statement, brief, or PRD references "what customers want" or "what the data shows" without grading the signal.
- Phase 2 of another skill needs an evidence dimension probed harder.
- A decision is being made that hinges on whether the evidence supports it.

## How to use

### Read first

Identify which artifact the evidence belongs to. If `~/Documents/pm-coach/problems/<slug>/notes.md` (or the equivalent for whatever artifact is in play) exists, read it for prior evidence work.

This skill **does not own its own folder.** It appends a dated audit entry into the `notes.md` of whichever artifact is being scrutinized.

### The audit

For every distinct evidence claim, tag along five dimensions:

| Dimension | Strong | Weak |
|---|---|---|
| **Behavior vs stated** | Observed actions, workflows, telemetry | What customers said in surveys or calls |
| **Plural vs singular** | Multiple independent sources, consistent | One vocal customer, one anecdote |
| **Representative vs vocal** | Drawn from the segment we actually want to grow | Self-selected, loudest, or atypical |
| **Observation vs interpretation** | What happened, specifically | The team's reading of why it happened |
| **External vs internal** | Customer-grounded data | Internal intuition, opinion, or proxy |

For each claim, also score the gap:

- **Treated stronger than it is** — most common failure. Anecdote presented as segment-level signal.
- **Treated weaker than it is** — less common. Real behavior dismissed because it's inconvenient.
- **Treated about right** — strength and treatment match.

### Phase 1 / Phase 2 / Land applied to evidence

**Phase 1 — Surface the evidence:**

- What evidence are you actually relying on for this claim? List each piece distinctly.
- For each piece — what kind, how many sources, how consistent across them, how representative of the segment we care about?
- What's the most charitable interpretation of what you've observed? The least charitable?
- What would you need to see to believe you're wrong?

**Phase 2 — Name the gaps:**

Commit to a position. For each piece of evidence, name the dimension where it's weakest and call out treatment that exceeds strength. Be direct.

Example phrasings:
- *"You're calling that 'segment evidence,' but it's three calls with the same industry. That's a candidate signal for one industry, not a segment-level claim."*
- *"That's a stated preference, not a behavior observation. Their workaround tells a different story."*
- *"You're treating internal team opinion as customer evidence. Those aren't the same thing."*
- *"One customer is loud. That doesn't make them representative. What's the rest of the segment doing?"*
- *"The data shows the correlation. It doesn't tell you why. The interpretation is doing all the work in this claim."*

Then identify **the one or two evidence claims that, if wrong, collapse the position**. Surface them as the highest-leverage things to verify.

**Phase 3 — Land:**

State: (1) the strongest version of what the evidence does support, (2) the weakest claim that's load-bearing, (3) the cheapest next observation that would reduce the most uncertainty.

## Output: the audit entry

Append into the relevant artifact's `notes.md`:

```markdown
## YYYY-MM-DD — Evidence audit

**Artifact under review:** <path-to-artifact>

### Claim-by-claim audit

| Claim | Behavior/stated | Plural/singular | Rep/vocal | Obs/interp | Ext/internal | Treatment |
|---|---|---|---|---|---|---|
| <claim 1> | ... | ... | ... | ... | ... | <stronger/weaker/about right> |
| <claim 2> | ... | ... | ... | ... | ... | ... |

### Load-bearing weak claims

The one or two claims that would collapse the position if wrong:
- <claim>: <what's weak about it, what would settle it>

### Cheapest next observations

- <thing to observe> would shift confidence on <claim> by <how much>.
```

Confirm with the PM before writing the audit into the artifact's `notes.md` — *"Want me to drop this audit into `<artifact>/notes.md`?"*

## Memory behavior

- Does **not** create its own folder.
- Appends to `notes.md` of the artifact being audited (e.g., `problems/<slug>/notes.md`, `business-cases/<slug>/notes.md`).
- Reads existing notes to avoid re-auditing what's already been audited recently.

## External context (MCP-aware)

- **`~~customer-conversations`** — when a claim is grounded in a specific call, fetch and verify the actual content. Often the audit reveals the team has rounded a quote in a self-serving direction.
- **`~~analytics`** — verify behavioral claims against the actual data, where possible.
- **`~~tickets`** — verify "users keep complaining about X" claims against actual ticket volume and content.

Never paste raw data into the audit. Summarize with provenance.

## Anti-patterns this skill names

- **Anecdote inflation.** A single customer story scaled to a segment claim.
- **Stated-as-behavior.** "Customers want X" used as evidence when no behavior backs it.
- **Internal-as-external.** Team intuition presented as customer signal.
- **Vocal-as-representative.** The loudest customer's view treated as the segment's.
- **Interpretation-as-observation.** Why we think it happened conflated with what actually happened.
- **Confidence inflation.** Tentative observation written up as established fact.
- **Hope as evidence.** Reasoning from what we want to be true rather than what we've seen.
- **Cherry-picked confirmation.** The audit only catches evidence that supports the position, not evidence that contradicts it.

## Tone

Direct, blunt where blunt is warranted, never sneering. The point isn't to embarrass — it's to make the gap between strength and treatment visible so the PM can either gather better evidence or dial back the confidence. Strong opinions, weakly held: when the audit shows the evidence is *better* than the team's caveats suggested, say so.
