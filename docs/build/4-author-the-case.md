# Author the Case

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: the case plan that binds everything — authored and validated, deliberately **not run yet** (a plan that won't validate is a design problem; a plan that validates then misbehaves is a binding problem)
- Register the Action App now: standalone, beside the solution, an empty page plus its schema — and why the app build is worth delegating to a subagent
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3d · The case"
--8<-- "seeds/3d-case/prompt.md"
````

- The gates: `check_caseplan.py` (referential integrity) and `uip maestro case validate`; read the rules even when green
- Proof: the case diagram open in Studio Web
- Knowledge block — *when the task is larger than the context*: this is the largest build in the workshop, so context size matters more than ever. Models differ in window size and in how they behave as the window fills — some compensate for smaller windows remarkably well. The options that fit a large task into a small context: write as you go (compaction preserves only what is already written), names and keys into `PROGRESS.md` the moment they exist, self-contained pieces delegated to a subagent (the app, in this block), clear and resume from files. There are — and will always be — tasks larger than the largest context of the day; the craft is working so the limit doesn't matter.
