# Plan the Work

Block 2. The design says what the solution *is*; ten minutes now decide the order it gets built in. This is the cheapest block of the day — and the one place ordering mistakes surface before anything is built, instead of halfway through an afternoon.

## The prompt

````markdown title="Prompt — block 2 · Plan"
--8<-- "seeds/2-plan/prompt.md"
````

Steps:

- [ ] Load the uipath-planner skill; derive `tasks.md` from `sdd.md` at the seed root
- [ ] Order the tasks leaves-first: entity, agents, app registration all before the case
- [ ] Put a `Validate:` step on every generating task and a test task before every deploy
- [ ] Review top-to-bottom: nothing blocked by something further down
- [ ] Update `PROGRESS.md`

## What a good plan looks like

- **Leaves before consumers.** Nothing binds to something unbuilt: the claim record before anything writes to it, the seven Agents before the case that calls them. The least obvious leaf is the review app's *contract* — the case binds it, so the app is registered (empty page and all) before the case exists, and its screens come last of all, after real runs have produced real data. You'll see why when you get there.
- **Routing, not re-description.** Each task names which skill builds it and which `sdd.md` sections to read — nothing more. A task that re-explains the architecture is a second copy of the design; two copies of one fact always end up disagreeing.
- **A check after every creation.** Every generating task carries a `Validate:` step, and a test task sits before anything deploys. The plan carries the discipline the build will be too busy for.

## Review the plan

Read it top to bottom once and ask two questions:

1. Could someone work this list without opening the design to find out what comes next?
2. Does every dependency point *up* the list? One "blocked by" pointing down means the order is wrong — and it is far cheaper to move a line now than to discover it mid-build.

One more habit this file carries: each later block sets the `Status:` line of the tasks it finishes. By the end of the day, a reader scanning the status lines sees exactly what was built and what was consciously skipped — the file degrades into the truth.

## Proof

<!-- screenshot: tasks.md — the first ~10 tasks showing order, skill routing and Validate: lines -->

A list that runs top to bottom, from leaves to the case to the screens, with a check after every step that creates something.
