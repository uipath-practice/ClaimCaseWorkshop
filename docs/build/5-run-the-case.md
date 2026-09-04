# Run the Case (Block 3e)

The plan is checked but has never met a real claim. This block deploys it and finds out what it actually does. **Several deploy cycles is the normal shape of this block** — the discipline is that each cycle ends with a named defect and a fix, not with "tried again."

## The prompt

````markdown title="Prompt — block 3e · Run it"
--8<-- "seeds/3e-run/prompt.md"
````

Steps:

- [x] Compile the case plan to BPMN (`uip maestro case pack`)
- [x] Wire the RPA / Agent / connector task inputs and outputs
- [x] Recompile and validate
- [x] Solution pack, publish, deploy for the first time
- [x] Run the auto-settle claim (happy path, no human)
- [x] Run the four human routes (proceed/refuse at the first gate, approve/deny at the second)
- [x] Verify and fix all five routes; check the data landed on the claim record
- [x] Upload the solution to Studio Web
- [x] Update `PROGRESS.md`

## What agent will review

- **The clean claim is the acceptance run.** A claim with nothing wrong traverses the whole lifecycle unattended. No task ever appears. Read the **Data Fabric** record and the case instance's trace instead — the checks, the findings and the letter should be all there. A *flagged* clean claim means the Agents are wrong, not the case.
- **Four human routes, answered from the command line.** The app has no screens yet and doesn't need them. A route that misbehaves now is a case defect, and finding it before the screens exist is the objective.
- **One identity.** Single claim number spans the case, the three documents, the letters and the record's key.
- **Letters are logged, never sent.** No mail leaves the exercise — the notification process records every letter (claim, stage, recipient, subject, body) in a tenant-level entity. The reviewer's screen later will show the thread from it, and Verify will read decisions from it.
## Proof

<!-- screenshot: a live case instance — the timeline through analysis to Approved, no task raised -->

A clean claim goes in; a settled claim comes out, no human touching it and no task ever raised. Then all four human routes, each proven from the CLI, each landing its data on the record.
