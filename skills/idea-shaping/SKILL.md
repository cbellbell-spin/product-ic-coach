---
name: idea-shaping
description: >
  Activate when the conversation is about a half-formed product idea, pre-problem-statement.
  Trigger phrases: "I have an idea", "what if we", "shape this idea", "early-stage thought",
  "I've been thinking we should", "rough concept", "exploring the problem space", "should we
  even consider X", "I'm not sure how to frame this yet". Forces crayon-level exploration and
  applies the double-diamond rhythm. Produces three rough versions side-by-side. Hands off to
  problem-statement once an idea graduates.
---

# Idea Shaping

Take a half-formed idea through low-fidelity exploration before letting the team converge. The default failure mode is over-investing in a polished version of the first idea that seems to work. This skill prevents that by forcing **crayon-level** thinking and applying the **double diamond** rhythm — diverge on the problem, converge, then diverge on the solution, converge.

Uses the umbrella's Phase 1 → Phase 2 → Land mechanics, scoped to early-stage idea exploration.

## Modes

- **Critique** (default) — scoped to whether the idea has been shaped enough to invest further.
- **Draft** (when invoked) — produce three crayon-level versions of the idea side-by-side and surface the diamond phase the team is in.

## When to use

- The PM has an idea they want to think through before committing to discovery, a problem statement, or a brief.
- An existing draft is already polished but the underlying idea hasn't been stress-tested for whether it's worth pursuing.
- The team is converging too fast (or too slow) and the diamond rhythm is off.

## Lens-specific Read first

If a problem slug is already in the conversation, check `~/Documents/pm-coach/problems/<slug>/notes.md` for prior shaping. Pre-graduation crayon explorations live under an "Early shapes" header in that file.

If no slug exists yet, this is pre-graduation territory. Capture inline; once an idea graduates into a problem worth statement-ing, hand off to `problem-statement` (which creates `problems/<slug>/`).

## Lens-specific Phase 1 questions

- Describe this in two sentences a four-year-old would understand. What is it? Who's it for?
- What's the failure mode if you build the polished version of this and it doesn't land?
- Are we in the **first diamond** (still figuring out what the problem actually is) or the **second** (figuring out which solution shape fits the problem)? Most teams skip the first diamond entirely.
- What three different shapes could this take? Give me the simplest, the most ambitious, and one that comes from a different angle.
- Where's the pull toward the first idea coming from — investment, sunk cost, someone's enthusiasm? What would it take to genuinely consider an alternative?

## Lens-specific Phase 2 challenges

- **Polish over fidelity.** The team is iterating on visuals or copy when the underlying idea hasn't been crayon-tested.
- **First diamond skipped.** Converging on a solution before genuinely opening the problem space. The question "what is the problem actually?" hasn't been opened up.
- **Convergence without rigor.** Diverging endlessly without picking a problem to solve or a solution shape to test. Interesting thinking, nothing ships.
- **Anchor bias.** The first version that seems to work has gravitational pull. Alternatives are sketched-but-not-considered.
- **No "what would change my mind."** Each version isn't testable. There's no observation that would settle which version is right.
- **Solution-first.** The "problem" is being reverse-engineered from a solution someone wants to build.

Ground challenges in specifics. Example: *"You've described the polished version three times now. We haven't touched the question of whether this is one problem or three. Slow down — what's the simplest crayon version that captures the core?"*

When `/land` is invoked: state (1) the diamond phase the team is actually in, (2) the strongest version of the idea after challenge, (3) what would change your mind, (4) the next move — graduate to a problem statement, run a hypothesis test, kill it, or stay in shaping.

## Draft mode

Produce three crayon-level versions. Each is two sentences max plus one line of "what would change my mind" and one line of "what's different about this version."

**`early-shapes` template** (appended into `problems/<slug>/notes.md` or kept inline pre-graduation):

```markdown
## Early shapes — YYYY-MM-DD

**Diamond phase:** First (problem) | Second (solution) | unclear

### Shape A — <one-phrase tag>
Two sentences a four-year-old would understand.
- *What's different about this version:* <one line>
- *What would change my mind:* <one line>

### Shape B — <one-phrase tag>
Two sentences.
- *What's different about this version:* <one line>
- *What would change my mind:* <one line>

### Shape C — <one-phrase tag>
Two sentences.
- *What's different about this version:* <one line>
- *What would change my mind:* <one line>

### Reading between them
Which shape does the team have the most pull toward, and why? Is the pull about evidence or investment? What signal would let us pick?

### Next move
Graduate to problem-statement | run a hypothesis test | stay in shaping | park
```

Refuse to produce one polished version. Refuse to produce more than three. The point of crayon thinking is that low fidelity invites input — finished versions create defensive attachment to investment.

## Memory paths

This skill does not own its own folder. It writes into:

- `problems/<slug>/notes.md` — under an "Early shapes" header — when a problem slug exists.
- A scratch buffer in conversation when no slug exists yet. When the idea graduates, hand off to `problem-statement` which will create the folder; copy the early shapes into the new `notes.md`.

## Graduation criteria — when to hand off

An idea graduates from `idea-shaping` to `problem-statement` when:
- A specific customer slice is named (anchored to `customer-context/`).
- The problem (not the solution) can be stated in one paragraph.
- "What changes if solved" is concrete enough to test.
- A scope boundary exists — we know what's deliberately *not* in this problem.

Until those four hold, stay in shaping.

## External context (MCP-aware)

- **`~~customer-conversations`** — when a customer call seeded the idea, summarize and cite for grounding.
- **`~~docs`** — adjacent ideas, prior explorations, related strategies.

Light touch — at the shaping stage, too much context contaminates divergence. Pull only when the PM explicitly references a source.

## Anti-patterns

- **Polish-first.** Building a finished mockup or doc before the idea has been crayon-tested.
- **Single-shape commitment.** One version of the idea has been written up; alternatives haven't been seriously considered.
- **Diamond-skipping.** The problem hasn't been opened up; the team is already comparing solutions.
- **Endless divergence.** Lots of options, no convergence, nothing testable.
- **Investment-as-validation.** "We've already put work into this version" treated as evidence it's the right version.
- **No-falsification.** The idea has no "what would change my mind" — which means it's a belief, not a hypothesis.
