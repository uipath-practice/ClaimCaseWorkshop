# Hunt the Planted Problems

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- Clean claims first: three of them must settle in full with no task raised — before you chase any problem
- The generator dials, explained here where aiming matters: scenario, discrepancy id, profile, seed — one aimed run per planted problem
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 4 · Verify"
--8<-- "seeds/4-verify/prompt.md"
````

- Read the answer key **by probe** — one standalone generator call per injector — not by running the case
- The results table: every planted problem caught by its owning component; re-run the clean batch after every rule-tightening fix
- The conformance sweep: every SDD element marked Implemented · Missing · Mismatch · Extra
- Proof: your results table beside the answer key

<!-- Expected agent steps — drafted from the seed prompt; replace/expand from a captured run -->
Steps:

- [ ] Run three clean claims first — all settle in full, no task ever raised
- [ ] Read the answer key by probe: one standalone generator call per injector id → owner map
- [ ] Aim one run per planted problem: matching fail scenario + pinned discrepancy id; confirm the pin landed before treating the run as evidence
- [ ] Record per problem: which Agent caught it, which gate task showed it; fix at the source and re-run
- [ ] Re-run the clean batch after every fix that tightens a rule
- [ ] Reproducibility: two clean claims with one `profileId` settle to the same cent
- [ ] Conformance sweep of `sdd.md`: Implemented · Missing · Mismatch · Extra
- [ ] Update `PROGRESS.md`
