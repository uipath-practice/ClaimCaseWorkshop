# Verify

Every piece was checked as you built it. This section answers the only question left — **does the whole thing work?** — and then hands the solution over in a state someone else can run.

## Testing a long-running process

A claims case runs for days and crosses seven agents, a case plan, a data record and two human gates. No single check can see all of that, so the workshop has been layering three kinds all along:

| Layer | Examples you've used | What it can see | What it cannot |
|---|---|---|---|
| **Offline gates** | `check_sdd.py`, `check_extraction_keys.py`, `check_caseplan.py` | Shape, references, keys — before anything is deployed | Whether the thing behaves |
| **Platform gates** | `uip maestro case validate`, agent validation | What the runtime will refuse to load | What loads fine and misbehaves live |
| **Live runs** | The clean claim, the four routes | Real behaviour, one path at a time | Whether *every* path behaves — that's this block |

Two habits carry the section:

- **Every gate is a floor.** A schema validator knows the document is well-formed; a grader knows it is well-written; neither has any idea what you are building — both will pass a component that cannot work, with a number that feels like an answer. Run them because they're free, then answer the question no gate can: *does it do the thing?* — by running the thing.
- **The seams need their own checks.** Where one stage produces and the next consumes, neither side is incentivized to check the handover — the producer has finished and the consumer was told to trust. That is why this exercise's gates sit *between* stages, and why end-to-end runs exist at all: unit-proven pieces can still compose into a wrong whole.

Two questions from *The Work That Remains* make a good standing review of any design, this one included: *who supplies the checker here?* — and *what part of the system guarantees correctness when correctness is required?* If the answer to the second is "the model," the architecture is unsafe.

## The answer key

The generator writes, beside each claim's documents, a record of what it planted and what should happen. It has been off-limits until now for a simple reason: read earlier, it turns the build into copying. Read now, it is the oracle your results table is scored against.

## In this section

| Step | What it covers |
|---|---|
| [1. Hunt the Planted Problems](1-hunt-the-planted-problems.md) | Block 4 — clean claims first, then one aimed run per problem, scored against the key |
| [2. Hand It Over](2-hand-it-over.md) | Block 5 — pins, the as-built design, and a runbook for whoever runs it next |
