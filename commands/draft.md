---
description: Switch the active specialized skill from critique mode to draft mode. Pairs with implicit critique mode — just describe what you want pressure-tested.
---

Switch the active specialized skill into **draft mode**.

In draft mode, the skill produces an artifact in Chris's format rather than critiquing an existing one. Conversational intake, anti-polishing, rough first — invite critique once a draft exists.

Behavior:

- If the active specialized skill supports draft mode (most do — see the skill's frontmatter "modes" or its body), switch into it. Open with one or two questions to gather the inputs the artifact needs, then produce the draft.
- If the active skill is **critique-only** (e.g., `evidence-audit`, `adoption-as-signal`), say so briefly and stay in critique mode.
- If the umbrella is active and no specialized skill is in play, ask which artifact the user wants to draft and route to the relevant skill.

After producing a draft, hand control back to the user and offer to critique it (the skill flips back to critique mode on the next turn unless the user keeps drafting).

If `/quiet` is active, do not announce the mode switch — just behave accordingly.
