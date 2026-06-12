# PM Coach System Roadmap

This document tracks the 12 "ghost" skills listed in `product-ic-coach`'s routing table that don't exist on disk yet, plus one existing skill recommended for demotion. Treated as a forward-looking roadmap, not as currently-shipped functionality. A skill moves from "ghost" to "live" by being implemented in its target plugin.

**Source of truth for "what skills does the IC coach want to expose."** The other plugins reference this list when deciding what to build.

---

## Cross-plugin design

These two design decisions apply to the whole system, not to any one skill.

### Shared references (no fourth package)

Two reference files exist identically in both `product-ic-coach` and `product-leadership-coach`:

- `references/pm-operating-manual.md` (279 lines)
- `references/working-with-me.md` (124 lines)

**Approach: single source of truth, symlink locally, copy in the build step before zip-and-publish.** Cowork zips don't preserve symlinks, so the publish step must inline the file content.

- **Local dev:** symlink the canonical file from each plugin's `references/`
- **Build step:** a small script copies the canonical file into each plugin's `references/` before running the Cowork validators and zip
- **Validator compatibility:** `validate-cowork-plugin.py` and `test_plugin.py` only check file structure, not content — they don't care about symlinks vs copies

This avoids a fourth package while keeping the source of truth in one place. The two reference docs unique to leadership (`leading-a-product-org.md`, `pm-leveling-framework.md`) stay where they are — not shared.

### SDLC reads from `~/Documents/pm-coach/`

The three plugins form a system. They should be able to share knowledge across tool boundaries.

**The IC coach writes to a tree under `~/Documents/pm-coach/`:**

- `customer-context/<slug>/profile.md`, `log.md`
- `problems/<slug>/problem-statement.md`, `notes.md`, `links.md`
- `prioritization/<date>-<context>/snapshot.md`

**The SDLC system should read from this tree as an input source.** Concretely, the SDLC's Phase 1A (Opportunity Brief) should:

1. Before drafting, check if `~/Documents/pm-coach/customer-context/<segment>/profile.md` exists for the segment in play
2. If yes, surface what's known and link to it from the Opportunity Brief's customer-context section
3. If the segment is named but no profile exists, suggest the PM capture context first via `product-ic-coach`'s `customer-understanding` skill
4. Reference, don't duplicate — the Opportunity Brief links, doesn't inline

**Implications for the IC coach:**
- `customer-understanding`, `problem-statement`, and `prioritization` file formats are now a **contract** the SDLC system reads from. They need to be stable and machine-greppable
- Headers and section names should be treated as API, not just markdown for humans

**Implications for the SDLC system:**
- `phase-behavior.md` Phase 1A section needs a "Cross-Plugin Read" block
- `file-structure.md` should document the `~/Documents/pm-coach/` tree as an *input source* alongside the per-initiative folder
- New entry in `_state.md` schema: "Customer-context anchors" listing the pm-coach paths that informed this initiative
- The SDLC's `pd-new` command should ask "Is there an existing customer-context profile or problem statement in pm-coach to anchor this to?"

**Order of work:** the IC coach's `customer-understanding` profile format should be stabilized first (it's already the most mature). Then the SDLC's Phase 1A reads it. `problem-statement` and `prioritization` follow.

---

## The 12 ghost skills (+ 1 demotion)

Sorted by recommended build order. Highest leverage first — items 1–5 resolve existing ambiguity in the IC coach's portfolio (either demoting or absorbing ambiguous skills). Items 6, 7, 10 are no-ops that just need the IC coach routing table updated. Items 8, 9, 11 are real build work. Items 12, 13 are future/unlikely.

| # | Skill | Status | Target plugin | Target artifact / phase | Notes |
|---|---|---|---|---|---|
| 1 | `evidence-audit` (currently an IC skill — recommended for demotion) | demote-then-absorb | sdlc-system | Cross-cutting capability (absorb into existing Evidence Quality Assessment) | The IC coach's standalone skill is a *lens*, not a destination — it doesn't own its own folder. Five-dimension framework (behavior/stated, plural/singular, rep/vocal, obs/interp, ext/internal + "treated stronger than it is" gap) folds into SDLC's existing Evidence Quality Assessment section. IC coach keeps a one-line pointer for pre-artifact conversations |
| 2 | `hypothesis-design` | planned | sdlc-system | Phase 1A (Opportunity Brief) | Theory → Hypothesis → Experiment maps to the Opportunity Brief's "test design" / "riskiest assumption" sections. Reads from IC coach's `customer-understanding` for segment context |
| 3 | `business-case` | planned | sdlc-system | Gate 1B (Fund Validation) | "Two-pager investment ask" maps to the Opportunity Brief's investment section. Gate 1B is the decision point. Thin IC-side skill is unnecessary |
| 4 | `say-no` | planned | sdlc-system | Gate 2A (Prioritize/Park/Kill) and Gate 1A (Fund Validation/Kill) | The formal "no" is a gate decision, not a skill. The IC coach's framing ("constructing a defensible no with reason/alternative/tradeoff") is too thin without the gate context |
| 5 | `metrics-grounding` | planned | sdlc-system | `_metric_registry.md` discipline + Metric Continuity cross-cutting capability | North-star metric selection and ops-to-outcome confidence check are the *pre-phase* versions. The registry is the post-lockdown version. Build as a Phase 2A enhancement, not a separate skill |
| 6 | `product-brief` | planned (no-op) | sdlc-system | Phase 2A | Already canonical there. No separate skill needed. The IC coach routing row should be removed once this is confirmed; rely on the SDLC `pd-new` / `pd-resume` flow |
| 7 | `prd` | planned (no-op) | sdlc-system | Phase 4 | Already canonical there as `04_prd.md`. The "locked vs partner-open vs exploratory tiers" framing is a section of the PRD template, not a separate skill |
| 8 | `launch-readiness` | planned | sdlc-system | Phase 3 / Gate 3 (Release Readiness) | "Whether sales can sell, buyers understand why, users can adopt" are gate-3 readiness checks. The full version is the SDLC gate; the IC coach version (if kept) is just the pre-gate thinking tool |
| 9 | `adoption-as-signal` | planned | sdlc-system | Phase 5 (Signal Reports) | Signal reports are the structured version. "Why adoption is missing — product, training, change-management, wrong-buyer" maps to a signal-report section |
| 10 | `engineering-partnership` | planned (no-op) | sdlc-system | Phase 4 / OpenSpec | OpenSpec handoff IS the engineering partnership artifact. No separate skill needed |
| 11 | `review-prep-debrief` | planned (split) | product-leadership-coach + sdlc-system | Gate prep | Two distinct jobs conflated in the IC coach row: prep the *decision* (leadership — "stress-test my recommendation") vs verify *artifact completeness* (SDLC `pd-gate`). Build as two thin reference docs in each plugin, not a single skill |
| 12 | `product-strategy` | unplanned | product-leadership-coach | new skill | Org-level strategy. Belongs in leadership, not IC. The IC coach framing ("target market, core problem, competitive landscape, value prop, business goals") is more product-positioning than strategy. Build when there's demand |
| 13 | `audience-translation` | unplanned | TBD | TBD | "Producing exec / engineer / customer / frontline versions of the same message" — no clear home. Build only with evidence of repeated need. Lowest priority |

---

## Build / publish process for shared references

Suggested layout:

```
shared/                                                                 # canonical source
├── pm-operating-manual.md
└── working-with-me.md

product-ic-coach/
└── skills/product-ic-coach/references/                                 # nested under the umbrella skill
    ├── pm-operating-manual.md   # absolute symlink → /Users/chrisbell/projects/shared/pm-operating-manual.md
    └── working-with-me.md       # absolute symlink → /Users/chrisbell/projects/shared/working-with-me.md

product-leadership-coach/                                               # not yet local; no-op in script
└── (references layout TBD when local source appears)
```

Publish step (run before `validate-cowork-plugin.py` + `test_plugin.py` + zip):

```bash
./scripts/sync-shared-refs.sh
```

The script lives at `scripts/sync-shared-refs.sh` at the projects root. It detects the nested references/ path automatically, removes the symlinks, and copies the canonical files in as regular files (so the zip contains plain files, not broken symlinks). Idempotent — safe to run repeatedly. After publishing, restore the symlinks manually for dev, or skip if you don't need to edit the shared files again before the next publish.

---

## Cowork platform note: legacy commands

Both `product-ic-coach` and `sdlc-system` are flagged by the Cowork validator as using **legacy commands** that the platform intends to deprecate. This is a Cowork versioning concern, not a project design issue — the command set is correct as written. No action needed until Cowork publishes a deprecation date; at that point, migrate to the new command shape (TBD) and remove the old commands. `product-leadership-coach` likely carries the same flag once it's reviewed.

---

## Out of scope

- The 5 SDLC references (`file-structure.md`, `phase-behavior.md`, `gate-behavior.md`, `integration-stubs.md`, `openspec-handoff.md`) — they stay in SDLC only
- The 2 leadership-only references — they stay in leadership only
- Implementation details for the SDLC cross-plugin read — this doc captures the design; the code changes are tracked separately
