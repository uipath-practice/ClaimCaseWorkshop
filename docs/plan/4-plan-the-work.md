# Plan the Work

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- Why a plan block exists at all (~10 minutes; it catches ordering problems before they cost an hour)
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 2 · Plan"
--8<-- "seeds/2-plan/prompt.md"
````

- Review `tasks.md`: leaves before consumers; every generation task followed by a check; nothing blocked by something below it
- Proof: the task list as generated (excerpt)

<!-- Expected agent steps — drafted from the seed prompt; replace/expand from a captured run -->
Steps:

- [ ] Load the uipath-planner skill; derive `tasks.md` from `sdd.md` at the seed root
- [ ] Order the tasks leaves-first: entity, agents, app registration all before the case
- [ ] Put a `Validate:` step on every generating task and a test task before every deploy
- [ ] Review top-to-bottom: nothing blocked by something further down
- [ ] Update `PROGRESS.md`
