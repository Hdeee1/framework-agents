---
trigger: model_decision
description: "License compliance rules and ledger schema for external assets (images, icons, fonts, audio, 3D models, datasets) and third-party libraries."
---

# External Assets & Licensing Standards

Enforce license compatibility according to `Project Type` in `AGENTS.md`. If `Project Type` is still a placeholder or unspecified, default to the stricter **Commercial** rules.

## License Tiers (Ordered by Preference)

1. **Tier 1 — Public Domain / Dedication:** `CC0-1.0`, `Unlicense`, `PDDL`.
2. **Tier 2 — Permissive (Attribution Required):** `MIT`, `BSD-2-Clause`, `BSD-3-Clause`, `Apache-2.0`, `ISC`, `OFL-1.1` (fonts), `CC-BY-4.0`.
3. **Tier 3 — Weak Copyleft / File-Level Reciprocity:** `MPL-2.0`, `LGPL-2.1/3.0`, `CC-BY-SA-4.0`. Allowed only if obligation boundaries are documented in `docs/ASSETS.md` and approved by the project owner for `Commercial` projects.

## Policy by Project Type

- **Automatically Permitted:** Tier 1 and Tier 2 assets/libraries whose full license text is verified from the canonical upstream source (official repository `LICENSE` file, package metadata, or official asset page).
- **Restricted / Require Explicit Owner Approval:**
  - Tier 3 licenses in `Commercial` projects.
  - Non-Commercial licenses (`CC-BY-NC`, custom non-commercial terms): **Strictly forbidden** in `Commercial` projects; permitted in `Personal` projects only with explicit owner approval and an `[NC-ONLY]` tag in `docs/ASSETS.md`.
  - No-Derivatives licenses (`CC-BY-ND`): Permitted only if used verbatim without resizing, format conversion, font subsetting, or modification.
- **Strictly Forbidden in All Projects:**
  - Unlicensed assets, scraped web media, or "free download" items lacking an explicit license text.
  - Strong copyleft (`GPL`, `AGPL`) dependencies linked into proprietary/non-GPL projects.
  - Third-party copyrighted brand logos, game rips, commercial music/fonts without a valid license, or AI-generated clones of trademarked/copyrighted characters.

## Mandatory Asset Ledger (`docs/ASSETS.md`)

Record every external asset in `docs/ASSETS.md` **before** referencing it in code:

| Asset Name | Category | Canonical Source URL | SPDX / License | Attribution Required | Local Path | License File Path |
| ---------- | -------- | -------------------- | -------------- | -------------------- | ---------- | ----------------- |

- Save required license texts and attribution notices under `assets/licenses/<asset-name>-LICENSE.txt`.
- Use `.agents/skills/asset-sourcing/SKILL.md` for the step-by-step acquisition workflow.
