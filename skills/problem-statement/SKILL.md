---
name: problem-statement
description: >
  Activate when the conversation is about defining, sharpening, or critiquing a specific problem
  worth solving. Trigger phrases: "the problem is", "I want to solve", "here's the problem
  statement", "is this the right problem", "draft a problem statement for", "is this a problem
  or a symptom", "what problem are we actually solving", "scoping the problem", "we need a
  problem statement for X".
  Each problem statement is scoped to ONE problem and grounded in the customer-understanding
  repository. One customer-context produces many problem statements over time. For macro-level
  customer context, use customer-understanding.
---

# Problem Statement

Sharpen a single problem worth solving for a specific customer slice. A problem statement must be **grounded in the customer-understanding repository** but explicitly does *not* need to address everything in it — pick the slice this problem covers, name what's deliberately out of scope, and link back.

## Modes

- **Critique** (default when an existing statement or claim is on the table) — pressure-test root vs symptom, segment coherence, behavior vs ask, scope.
- **Draft** — produce a sharp problem statement using the template below.

## When to use

- The PM is articulating a problem to solve (verbally or in writing).
- The PM is reviewing a draft problem statement, opportunity brief, or PRD's problem narrative.
- A specific problem needs to be carved out of broader customer context.
- A problem statement needs scope defined — what it covers and what it doesn't.

## How to use

### Read first

Before engaging:

1. Identify the customer / segment in play. Check `~/Documents/pm-coach/customer-context/<slug>/` for the relevant profile and recent log entries.
2. If a `problems/<slug>/` folder already exists for this problem, read `problem-statement.md`, `notes.md`, and `links.md`.
3. If neither exists, surface that gap. *"I don't see existing context for this customer in the repository. Want to capture that first via `customer-understanding`, or proceed and we'll capture context inline?"*

### Critique mode (Phase 1 / Phase 2 / Land)

**Phase 1 — Draw out the statement:**

- Who specifically has this problem? Tie it to a slice of the customer-understanding repository, by name.
- How are they solving it today? What does the workaround tell you about what actually matters?
- Is this the actual problem, or a symptom of something upstream?
- What changes about their day if this is solved? What stays the same?
- What's deliberately *not* in scope here? What part of the customer-context are we choosing not to address with this problem statement?

**Phase 2 — Challenge:**

Common vulnerabilities in problem statements:
- **Symptom dressed as problem.** The stated problem is the visible artifact, not the upstream cause.
- **Two segments in one statement.** What looks like one customer is actually two, with conflicting needs that will pull the solution apart.
- **Feature request as problem.** "Users want X feature" is not a problem statement. The problem is what X would solve.
- **Behavior contradicts ask.** Customer says they want X but their workaround reveals they don't actually act on the related friction.
- **Floating from customer-understanding.** The statement makes claims about the customer that aren't anchored to repository entries — or worse, contradict them.
- **No out-of-scope.** Every problem statement that covers everything covers nothing. If you can't say what's out of scope, the statement is too broad.
- **Pre-baked solution.** The problem has been written backward from a solution the team already wants to build.

Ground challenges in the actual customer-context entries. Example: *"Your statement says enterprise users are stuck with manual reconciliation, but the profile log only references that pain in the SMB segment. Which one is this for?"*

**Phase 3 — Land:**

State the sharpest version of the problem, the customer-context anchors it draws on, what's deliberately out of scope, the strongest objection that survives, and the cheapest next observation that would confirm or shift the framing.

### Draft mode

Produce a problem statement in the structure below. Anti-polishing — rough first.

**`problem-statement.md` template:**

```markdown
# Problem: <short slug>

**Last updated:** <YYYY-MM-DD>
**Status:** <draft | sharpened | parked>

## The problem (one paragraph)

A specific, named slice of customer experience that we believe is worth solving. Who feels it (with segment/account anchored to the customer-context repository), what they're trying to do, why the current path fails them.

## Customer-context anchors

Which entries in `customer-context/` ground this problem:
- [<segment-or-account>/profile.md](../../customer-context/<slug>/profile.md) — section on X
- [<segment-or-account>/log.md](../../customer-context/<slug>/log.md) — entry from YYYY-MM-DD: <short>

## Evidence summary

What we've actually observed (not what we've assumed). Behavior > stated request. Plural > singular. Representative > vocal.

## What changes if solved

The specific behavior or outcome that improves. Be concrete enough to test.

## What's deliberately out of scope

Other parts of the customer-context this statement does NOT address. Naming these prevents scope creep and clarifies that this is one of many problem statements that may emerge from the same underlying customer understanding.

## Open questions

What we still need to learn before this statement is solid. Tag with the cheapest way to learn.
```

### Update mode

When the user comes back with new information, update `problem-statement.md` in place (confirm diff before overwriting per global CLAUDE.md). Append a dated entry to `notes.md` describing what changed and why.

## Memory paths

```
~/Documents/pm-coach/problems/<slug>/
├── problem-statement.md      # canonical
├── notes.md                  # append-only thinking log
└── links.md                  # cross-refs (customer-context, strategy, brief, PRDs)
```

**`links.md` format:**

```markdown
# Links — <problem slug>

## Upstream
- Customer context: `customer-context/<slug>/profile.md`
- Strategy: `strategies/<area>/strategy.md` (if applicable)

## Downstream
- Brief: `briefs/<area>/product-brief.md`
- PRD: `prds/<feature>/prd.md`
- Hypotheses: `hypotheses/<slug>/hypothesis.md`
```

Update `links.md` whenever a new artifact references this problem.

## Relationship to customer-understanding

**Strict rule**: this skill never duplicates customer context inline. It links / refers, keeping `customer-understanding` as the single source of truth. If material customer-context is missing or stale, push the PM to update it via `customer-understanding` before sharpening the problem statement.

## External context (MCP-aware)

- **`~~customer-conversations`** — when a conversation grounded the problem, summarize and cite (date + source). Provenance into `notes.md`, not raw paste.
- **`~~docs`** — existing problem framings or opportunity briefs the PM points at.
- **`~~tickets`** — support tickets that reveal problem frequency or severity.

## Anti-patterns this skill names

- **Symptom in problem-statement clothing.** Probing further reveals the stated problem is downstream of the real one.
- **Two-segment merge.** "Mid-market and enterprise users both struggle with X" — usually they don't, or not in the same way.
- **Feature-request masquerade.** "Users need bulk export" is not a problem.
- **Solution backflow.** Statement was reverse-engineered from a solution the team already picked.
- **Floating from repository.** Claims about the customer with no anchor to `customer-context/`.
- **No out-of-scope.** Statement is too broad; everything important is implicitly in.

## Tone

Direct. Grounded in the actual customer-context entries and the actual problem in play. Never generic. When evidence is anecdotal, name it. When the statement is a symptom, name the upstream problem you suspect.
