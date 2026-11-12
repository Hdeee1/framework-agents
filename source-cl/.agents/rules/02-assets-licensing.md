---
trigger: model_decision
description: "License policy and ledger schema for external assets (images, icons, fonts, audio, 3D models, datasets) and third-party libraries."
---

# External Assets & Licensing

Apply the column matching `Project Type` in `AGENTS.md`. If it is unfilled, use **Commercial**.

## License Tiers

1. **Tier 1 (public domain):** `CC0-1.0`, `Unlicense`, `PDDL`.
2. **Tier 2 (permissive, notice/attribution kept):** `MIT`, `BSD-2-Clause`, `BSD-3-Clause`, `Apache-2.0`, `ISC`, `OFL-1.1` (fonts), `CC-BY-4.0`.
3. **Tier 3 (weak copyleft):** `MPL-2.0`, `LGPL-2.1/3.0`, `CC-BY-SA-4.0`.

## Policy

| License class                                                                                                                                     | Personal                                                                      | Commercial                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Tier 1, Tier 2                                                                                                                                    | Allowed                                                                       | Allowed                                                         |
| Tier 3                                                                                                                                            | Allowed; record obligations in `docs/ASSETS.md`                               | Owner approval required; record obligations in `docs/ASSETS.md` |
| Non-commercial (`CC-BY-NC`, custom NC terms)                                                                                                      | Owner approval required; tag `[NC-ONLY]` in `docs/ASSETS.md`                  | Forbidden                                                       |
| No-Derivatives (`CC-BY-ND`)                                                                                                                       | Verbatim use only (no resize, conversion, subsetting)                         | Verbatim use only                                               |
| Strong copyleft (`GPL`, `AGPL`)                                                                                                                   | Forbidden unless the project's own `LICENSE` is a compatible copyleft license | Same                                                            |
| Unlicensed, scraped, "free download" without license text, trademarked logos, game rips, unlicensed music/fonts, clones of copyrighted characters | Forbidden                                                                     | Forbidden                                                       |

- Verify the license text from the canonical source (official repository `LICENSE`, package metadata, or official asset page). Search filters and badges are not proof.
- A permitted license does not approve a new dependency. Dependency approval is governed by `00`.

## Asset Ledger (`docs/ASSETS.md`)

Record every external non-library asset **before** referencing it in code. Record a library only if it is Tier 3 or approved as an exception; other libraries are tracked by the lockfile.

| Asset Name | Category | Canonical Source URL | SPDX / License | Attribution Required | Local Path | License File Path |
| ---------- | -------- | -------------------- | -------------- | -------------------- | ---------- | ----------------- |

- Store required license texts in `<Assets Directory>/licenses/<asset-name>-LICENSE.txt`.
- Acquisition steps: `.agents/skills/asset-sourcing/SKILL.md`.
