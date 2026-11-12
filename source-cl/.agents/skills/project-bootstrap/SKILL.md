---
name: project-bootstrap
description: "Initializes a brand-new empty repository: layout, tooling, tests, docs, and populated AGENTS.md. Use only when starting a project from scratch in an empty workspace."
---

# Project Bootstrap

1. **Confirm the repo is empty** using the definition in `.agents/rules/00-core-and-boundaries.md`. If not, run `project-onboard` instead.
2. **Confirm inputs.** Required: language, framework (or none), `Project Type`, and a one-sentence description of the product. Ask for any that are missing. Do not choose a stack on your own.
3. **Version control & editor config:** initialize Git if absent; create a stack-appropriate `.gitignore`, `.editorconfig`, and the runtime pin file.
4. **Scaffold directories:** idiomatic source and test directories, plus `docs/` and the assets directory.
5. **Configure toolchain:** package manager with a committed lockfile, strict linter, formatter, type-checker (if applicable), test runner. The user's confirmation in step 2 is approval for these toolchain dependencies; list them in `docs/DECISIONS.md`.
6. **Create docs:** `README.md` (setup and run), `.env.example`, `docs/DECISIONS.md` (initial stack decision, format from `01`), `docs/ASSETS.md` (ledger header from `02`).
7. **CI and container files:** create only if the user asked or the deliverable type requires them, following `.agents/rules/06-delivery.md`.
8. **Populate config:** replace every placeholder in `AGENTS.md` and `.agents/rules/03-lang-stack.md` with exact project values. Keep all sections and headings. Set `Known Baseline Failures` to `None`.
9. **Smoke test:** add one deterministic smoke test. Run the Verification Gate (`00`) until it passes. Run `grep -n "<PLACEHOLDER:" AGENTS.md .agents/rules/03-lang-stack.md` and confirm no output.
10. **Initial commit** on the default branch: `chore: bootstrap project`.
11. **Stop.** Do not implement product features here; they go through `.agents/workflows/new-feature.md`.
