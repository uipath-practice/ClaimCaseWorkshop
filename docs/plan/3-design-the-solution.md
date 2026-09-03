# Design the Solution

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: turn the PDD into an architecture an architect could hand over — one `sdd.md`, fixed name
- The prompt (transcluded from the seed — paste it into your coding agent):

````markdown title="Prompt — block 1 · Design"
--8<-- "seeds/1-design/prompt.md"
````

- What the planner does, and why it asks nothing
- Review the generated SDD: structure, key sections, what to check by hand
- The gate: `check_sdd.py` — one command runs the planner's own audit and the process cross-check; read its rules even when it passes
- Proof: what a passing design looks like (SDD excerpt screenshot)

<!-- Expected agent steps — drafted from the seed prompt; replace/expand from a captured run -->
Steps:

- [ ] Read `PDD.md`, `CONFIG.md` and `contracts/` (components, claim entity, review task, provided processes)
- [ ] Load the uipath-planner skill; run autonomous, design only
- [ ] Write `sdd.md` at the seed root, with `Tasks file: tasks.md` in the handoff header
- [ ] Add the two sdd-addendum sections (entity write-ownership matrix; design feedback to PDD)
- [ ] Run the gate: `python3 1-design/check_sdd.py sdd.md --pdd PDD.md` — fix findings, rerun until clean
- [ ] Update `PROGRESS.md`
