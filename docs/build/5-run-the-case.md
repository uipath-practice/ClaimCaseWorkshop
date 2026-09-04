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
- [x] Upload the solution
- [x] Update `PROGRESS.md`

## What to review

- **The clean claim is the acceptance run — and zero tasks is the pass.** Only a claim with nothing wrong traverses the whole lifecycle unattended, so it is the one run that proves the case end to end. The first time it works it looks like nothing happened: no task ever appears. Read the **Data Fabric** record and the case instance's timeline instead — the checks, the findings and the letter are all there. A *flagged* clean claim means the Agents are wrong, not the case.
- **Four human routes, answered from the command line.** The app has no screens yet and doesn't need them — the case bound its *contract* at 3d. A route that misbehaves now is a case defect, and finding it before the screens exist is the point.
- **One deployment, redeployed in place.** A second deployment "to prove it runs elsewhere" loses every running instance and proves nothing Verify won't. Promotion is the same package in another tenant with that tenant's config — described at handover, never done here.
- **One identity.** The case is created first and hands its id to the generator, so a single claim number spans the case, the three documents, the letters and the record's key.
- **Letters are logged, never sent.** No mail leaves the exercise — the notification process records every letter (claim, stage, recipient, subject, body) in a tenant-level entity. The reviewer's screen will show the thread from it, and Verify will read decisions from it.

!!! note "Remember"
    - **Read the instance, not the job list.** The case's variables and timeline answer what a job status cannot.
    - **If you know what the output should be, assert it; if you don't, read it.** By the fifth deploy cycle the loop deserves a script — and the script asserts the things that lie: an exit code 0 with a failure payload, a deploy that shipped a stale artifact, a listing that returned only its first page.
    - **A wait needs a verified wake.** The case runs for minutes and tasks appear on their own time. Before waiting, your agent should state exactly what will wake it and prove that check fires once; after waking, re-check the real state rather than trusting the notification.

## Proof

<!-- screenshot: a live case instance — the timeline through analysis to Approved, no task raised -->

A clean claim goes in; a settled claim comes out, no human touching it and no task ever raised. Then all four human routes, each proven from the CLI, each landing its data on the record.
