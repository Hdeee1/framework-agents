---
name: asset-sourcing
description: "Finds, verifies licenses, downloads, and logs external assets (images, icons, fonts, audio, 3D models, datasets). Use whenever a task requires adding third-party static assets from outside the workspace."
---

# Asset Sourcing

## Procedure

1. **Define Requirements:** Specify asset category, target format (prefer SVG for icons, WebP/AVIF for raster images, WOFF2 for fonts, OGG/MP3 for audio), dimensions, and usage context.
2. **Check License Policy:** Read `.agents/rules/02-assets-licensing.md` and verify `Project Type` in `AGENTS.md`.
3. **Verify Upstream License:** Locate the asset on a canonical source and read the full license text (never rely solely on search filters or summary badges).
4. **Filter Candidates:** Accept Tier 1 and Tier 2 licenses automatically. Reject forbidden licenses or request explicit owner approval for Restricted / Tier 3 licenses per `.agents/rules/02-assets-licensing.md`.
5. **Download & Organize:** Save the asset under `assets/{images,icons,fonts,audio,models,data}/` using lowercase `kebab-case` filenames without spaces.
6. **Store License Proof:** Save the upstream license text and attribution notice to `assets/licenses/<asset-name>-LICENSE.txt` whenever attribution or license inclusion is required.
7. **Update Ledger:** Add a complete entry to `docs/ASSETS.md` before referencing the asset in code.
8. **Optimize Safely:** Compress media or subset fonts only if the license permits derivative works (never modify `No-Derivatives` assets).
9. **Reference Cleanly:** Import or reference the asset path via a named constant or configuration module rather than scattering hardcoded path strings.
