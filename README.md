# Product IC Coach

A rigorous thought partner *and* craft companion for individual contributor PMs. Pressure-tests product thinking and drafts artifacts in Chris's format — grounded in his PM operating manual, not generic frameworks.

Not for: people management, org design, leadership decisions, or leveling conversations. Use `product-leadership-coach` for those. For initiative execution through stage-gate, use `sdlc-system`.

## How it's structured

- **Umbrella skill** (`product-ic-coach`) — generic entry point; runs the Phase 1 / Phase 2 / Land coaching mechanics; routes to specialized skills when a specific lens is in play.
- **Specialized skills** — each tied to a specific framework from Chris's PM operating manual. Most support both **critique** (pressure-test an existing draft) and **draft** (produce an artifact in Chris's format). A few are critique-only (e.g., `evidence-audit`, `adoption-as-signal`).
- **Persistent memory** — the plugin maintains its own state across sessions in `~/Documents/pm-coach/`. Customer context accumulates over time; problem statements, briefs, PRDs, hypotheses, prioritization snapshots are written to predictable paths and updated rather than re-created.
- **Session artifacts (Mann pattern)** — each problem slug carries `brief.md` (coaching spec) and `decisions.md` (append-only editorial log). `/open` loads these at session start; `/close` deposits the session's decisions. The umbrella auto-triggers `/open` when a known slug is referenced.

## Commands

| Command | What it does |
|---------|-------------|
| `/open [slug]` | Session-start ritual — load brief + decisions for a problem, surface state, skip Phase 1 warm-up |
| `/close` | Session deposit — reflector pass, propose decisions.md entries, ask if brief needs updating |
| `/think` | Return to Phase 1 Socratic mode |
| `/challenge` | Flip adversarial — steelman the opposition and attack the current position |
| `/harder` | The pushback wasn't hard enough. Go further |
| `/land` | Force synthesis — commit to a recommendation |
| `/draft` | Switch the active specialized skill from critique to draft mode |
| `/recap` | Summarize the current position and strongest challenge |
| `/solid` | Signal that you're confident and ready to move forward |
| `/stuck` | Stay in Phase 1 longer — position isn't clear yet |
| `/reset` | Start fresh on a new topic |
| `/quiet` | Toggle command suggestions on/off |

## Specialized skills (Phase A — available now)

| Skill | What it does |
|---|---|
| `customer-understanding` | Macro-level, persistent. Builds and maintains a living customer-context repository (segments and accounts) that other skills read from. Buyers vs. users, the critical 15-20%, picking the right customers, fit signals. |
| `problem-statement` | Sharpens a single problem worth solving for a specific customer slice. Grounded in `customer-understanding` (one-to-many: one customer profile → many problem statements). Forces named out-of-scope. |
| `evidence-audit` | Cross-cutting critique-only lens. Grades signal quality across five dimensions (behavior/stated, plural/singular, representative/vocal, observation/interpretation, external/internal) and names the gap between strength and treatment. |
| `idea-shaping` | Forces crayon-level thinking and applies the double-diamond rhythm. Produces three rough versions side-by-side. Refuses to polish before the idea has been stress-tested. Hands off to `problem-statement` once an idea graduates. |
| `prioritization` | Ranks investments using **Return × Risk × market expectation** — explicitly anti-RICE. Forces capacity reality (often <20% available for new feature work) and named tradeoffs. Snapshots are dated and append-only. |

More skills land in subsequent phases (`hypothesis-design`, `product-strategy`, `business-case`, `product-brief`, `prd`, `launch-readiness`, `adoption-as-signal`, `metrics-grounding`, `say-no`, `audience-translation`, `engineering-partnership`, `review-prep-debrief`).

## Plugin memory

The plugin reads and writes to `~/Documents/pm-coach/` — a structured tree of customer context, problem statements, strategies, briefs, PRDs, hypotheses, prioritization snapshots, launches, metrics, reviews, and session logs.

```
~/Documents/pm-coach/
├── INDEX.md                              # auto-maintained table of contents
├── customer-context/<segment-or-account>/{profile.md, log.md}
├── problems/<slug>/{brief.md, decisions.md, problem-statement.md, notes.md, links.md}
├── strategies/<area>/{strategy.md, notes.md}
├── briefs/<area>/{product-brief.md, notes.md}
├── business-cases/<slug>/{business-case.md, notes.md}
├── prds/<feature>/{prd.md, notes.md}
├── hypotheses/<slug>/{hypothesis.md, notes.md}
├── prioritization/<yyyy-mm-dd>-<context>/snapshot.md
├── launches/<feature>/{readiness.md, adoption-notes.md}
├── metrics/<area>/metrics-tree.md
├── reviews/<yyyy-mm-dd>-<slug>/{prep.md, debrief.md}
└── sessions/<yyyy-mm-dd>.md
```

### Memory rules every skill follows

- **Read first, then engage.** Skills load relevant existing artifacts before pressing on with new questions.
- **Update, don't duplicate.** When a slug/topic exists, update the canonical `*.md` rather than creating a new one. Versioning is via git, not file proliferation.
- **Notes are append-mostly.** Dated entries; don't rewrite prior content.
- **Cross-link explicitly.** Artifacts point at the upstream artifacts they depend on. A PRD lists the brief and problem statement it implements; a problem statement lists the customer-context entries it draws on.
- **Confirm before destructive writes.** Per global CLAUDE.md, propose the diff and confirm before overwriting canonical state.
- **Sensitive-data hygiene.** Names and roles only — no contracts, no financial data, no raw transcripts. Summarize MCP-pulled content with provenance; don't paste raw.

### Philosophy memory vs. project memory

- **Philosophy memory** lives in this plugin's `skills/product-ic-coach/references/` (the operating manual, working-with-me). Single source of truth for the standards being applied. Internalized, never cited by name.
- **Project memory** lives in `~/Documents/pm-coach/`. State of Chris's actual product work.

## MCP integration

Specialized skills know how to opportunistically pull from connected MCPs and gracefully degrade when they're not present. Functional categories (not specific tool names) are referenced:

- `~~customer-conversations` — Granola, Fireflies
- `~~docs` — Google Drive, Notion, Atlassian
- `~~tickets` — Linear, Asana, Jira, ClickUp, Monday
- `~~analytics` — Amplitude, Pendo
- `~~chat` — Slack

Behavior: never silent background scanning. The user explicitly references a source, or the skill names what would help and asks. All MCP-pulled material is summarized into the relevant `notes.md` with provenance, never raw-pasted — keeps memory portable and inspectable when MCPs disconnect.
