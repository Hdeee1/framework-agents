---
name: asset-sourcing
description: "Finds, verifies licenses, downloads, and logs external assets (images, icons, fonts, audio, 3D models, datasets). Use whenever a task adds third-party static assets from outside the workspace."
---

# Asset Sourcing

1. **Check network access.** If the environment cannot download files, stop and ask the user to provide the asset.
2. **Define requirements:** category, format (prefer SVG for icons, WebP/AVIF for raster images, WOFF2 for fonts, OGG/MP3 for audio), dimensions, usage context.
3. **Read policy:** `.agents/rules/02-assets-licensing.md` and `Project Type` in `AGENTS.md`.
4. **Verify license** from a canonical source by reading the full license text.
5. **Filter:** accept what the policy table allows; ask the owner for approval where it says approval is required; reject forbidden classes.
6. **Download** into `<Assets Directory>/{images,icons,fonts,audio,models,data}/` with lowercase `kebab-case` filenames.
7. **Store license proof** in `<Assets Directory>/licenses/<asset-name>-LICENSE.txt` whenever attribution or license inclusion is required.
8. **Update ledger:** add a full row to `docs/ASSETS.md` before referencing the asset in code.
9. **Optimize** (compress, subset) only if the license permits derivatives.
10. **Reference** the asset through a named constant or config module, not scattered path strings.
