# Run the Case

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: deploy the case and prove it moves — one deployment, redeployed in place
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3e · Run it"
--8<-- "seeds/3e-run/prompt.md"
````

- What to review: the claim number comes from the case; letters are logged, never sent
- Done when: a clean claim settles with **no task raised**, and all four human routes work
- Proof: a live instance


Steps:

- [ ] Compile the case plan to BPMN (`uip maestro case pack`)
- [ ] Wire the RPA / Agent / connector task inputs and outputs
- [ ] Recompile and validate
- [ ] Solution pack, publish, deploy for the first time
- [ ] Run the auto-settle claim (happy path, no human)
- [ ] Run the four human routes (proceed/refuse at the first gate, approve/deny at the second)
- [ ] Verify and fix all five routes; check the data landed on the claim record
- [ ] Upload the solution
- [ ] Update `PROGRESS.md`