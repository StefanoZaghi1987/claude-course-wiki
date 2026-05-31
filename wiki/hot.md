## [2026-05-31]

Expanded `wiki/pages/spec-driven-development.md` with a full `## Deep dive` section. Read all
four source PDFs in their entirety (manuale-prima, terza, quarta, quinta lezione). The deep dive
covers: the paradigm inversion argument, the four-approach model and the "stone" metaphor, all
five principles with their mutual dependencies and failure modes, the seven-component spec schema
with the EV-002 quantitative evidence (35-line → 60-70% coverage vs. 150-line → ~95%), the two
workflow variants with the EV-003 one-day production case study, the three operational
configuration tiers (Lite / Intermediate / Advanced), CLAUDE.md modularization rationale,
Sub-Agent Driven Development execution trade-offs, advanced slash commands lifecycle, and a
limitations section including the "self-assessed coverage figures" caveat. Frontmatter updated
with `expanded: 2026-05-31`; `wiki/index.md` marked `(expanded)`; `wiki/log.md` appended.

Still open from previous session: no lint run done since vault was first populated — "(to be added)"
source references in some early pages are now resolvable; `wiki/compass.md` still does not exist.

Next: run `/lint` to catch dead links and resolve the "(to be added)" stubs, then run `/reflect`
to create `compass.md` — the vault now has enough depth to make a reflect meaningful.
