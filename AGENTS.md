# Ventuno Q Workspace

Hardware project workspace for Illia's three Arduino VENTUNO Q boards (SKU ABX00181).
Code-heavy work happens in `firmware/` (sketches, sketches-side code, experiments); this repo is the knowledge base + project memory.

## Layout
- `kb/` — the VENTUNO Q knowledge base (board facts, setup notes, pitfalls). Living documents, topic-named.
- `kb/evidence/` — raw source captures (official page dumps, datasheet extracts) that kb/ notes cite. Unedited originals.
- `notes/` — dated project notes (`YYYY-MM-DD-topic.md`): experiments, findings, observations from the physical boards.
- `notes/decisions.md` — decision log: Date | Decision | Rationale | Revisit when.
- `firmware/` — sketches/experiments for the boards; one subdir per experiment once there is more than one.

## Conventions
- Every kb/ note states its **source** (URL of what was captured in evidence/) and **capture date**.
- Specs not backed by a file in `kb/evidence/` are marked **NEEDS VALIDATION**.
- Vendor marketing copy is not fact: distinguish "spec table" facts from "Assumption"/marketing claims.
- Board-specific discoveries from the physical units go in dated notes first, then get promoted to kb/ once confirmed.
- File naming: `YYYY-MM-DD-topic.md` for dated notes; topic-only names for living documents.

## Git
- Remote: https://github.com/blackprowler/ventuno-hermes.git (main). Commit after each meaningful step and push.
