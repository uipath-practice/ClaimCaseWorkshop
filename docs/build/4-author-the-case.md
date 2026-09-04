# Author the Case (Block 3d)

The **Maestro** case plan binds everything you have built into one lifecycle — and this block deliberately stops at *authored and validated*, never run. The split matters: a plan that will not validate is a **design** problem; a plan that validates and then misbehaves is a **binding** problem. Kept apart, each is debugged where it lives — merged, the second gets debugged through redeploy cycles at several minutes each.

*The Work That Remains* describes exactly this shape, with an insurance claim as its own example: the **case** owns the lifecycle (opened, investigating, decided, closed); the stable stretches inside a stage run as declared **workflow** on rails, exact and tokenless; and where a stretch needs judgement, an agent takes one well-defined **goal** and finds the path at runtime. The three nest — you are building all three at once.

## First: register the Action App

The two human gates are `action` tasks bound to the app's **contract** — `contracts/review-task.md` — not to its screens. So the app is registered *now*: standalone, beside the solution, an empty page plus its schema. That is enough for the case to wire both gateways and prove every route from the command line; the screens replace the empty page at 3f and the case is never touched again.

The contract is settled once and not revisited, because changing it after the case binds **clears the bindings at both gateways**. And the app build is a natural piece to delegate: one contract file defines its entire I/O, nothing about it needs this block's context — an agent with subagents builds it there; one without gets the same effect by sequencing app-first.

## The prompt

````markdown title="Prompt — block 3d · The case"
--8<-- "seeds/3d-case/prompt.md"
````

Steps:

- [x] Scaffold and deploy the Coded Action App `claim-review-<seat>` (beside the solution, stand-alone)
- [x] Build the case plan (`caseplan.json`) from `sdd.md`
- [x] Validate the case plan (`uip maestro case validate` + `check_caseplan.py`)
- [x] Upload the solution to Studio Web
- [x] Update `PROGRESS.md`

## What to review

- **Two outcomes at each gate — never three.** Carry on, or stop. *Partial approve* is a recommendation and an amount on the record, not a branch: route on what the process does next, not on what the answer was about. Two gates × two answers = the four routes the next block proves.
- **A gate opens because something needs a person, never as a formality.** A clean claim raises no task at all — and the skipped path still writes down that it was decided automatically, explicitly. An empty reason field downstream reads as "a reviewer approved everything," and nothing was reviewed.
- **Fail towards the human.** Unset, empty and false must all *open* a gate. A condition that quietly closes one on missing data is the most expensive kind of correct-looking plan.
- **One stage does nothing, on purpose.** *Missing details* is a known future requirement, modelled and deliberately unwired: one required placeholder task, entered on a condition nothing sets.

!!! note "When the task is larger than the context"
    This is the largest build in the workshop, so context matters more than ever. Models differ in window size and in how they behave as the window fills — some compensate for smaller windows remarkably well. What fits a large task into any window: **write as you go** (compaction preserves only what is already written), names and keys into `PROGRESS.md` the moment they exist, self-contained pieces delegated to a subagent (the app, in this block), clear and resume from files. There will always be tasks larger than the largest context of the day; the craft is working so the limit doesn't matter.

## The gates

```bash
uip maestro case validate
python3 3d-case/check_caseplan.py
```

Run **exactly these commands** — the full validator, then the shipped checker. The validator's errors are runtime failures spelled out in advance: a gate you route around does not go away, it fails later at several minutes per deploy cycle. And read the rules even on green — `validate` accepts several shapes that fail only on a live claim (a `skipCondition` does not stop a task being raised; two entry conditions are ANDed; `runs-sequentially` is not an ordering).

## Proof

<!-- screenshot: the case diagram open in Studio Web — stages, the two gates, the parallel analysis split -->

**The diagram is a deliverable.** A case plan a business reader cannot follow is a case plan nobody signs — open it in **Studio Web** and read it as they would.
