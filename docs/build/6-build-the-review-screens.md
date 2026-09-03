# Build the Review Screens

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: two reviewer screens, built last — against payloads your own agents produced
- Layout is decided (`layout.md`), styling tokens are given (`brand.md`); what remains is yours
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3f · Action App"
--8<-- "seeds/3f-validation/prompt.md"
````

- **The localhost review before the first publish — step by step**: the four gate/state URLs to open, what to look at in each, and how to hand feedback back to the agent before it publishes
- Done when: both gates render in a browser and a decision writes back
- Proof: the screen in Action Center
<!-- Expected agent steps — drafted from the seed prompt; replace/expand from the seat run when it reaches 3f -->
Steps:

- [ ] Read `PDD.md` §5.7, `contracts/review-task.md`, `3f-validation/layout.md` and `brand.md`
- [ ] Load the uipath-coded-apps skill; replace the registered app's empty page with the two gate screens
- [ ] Capture fixtures from your own Data Fabric records (never from `uip tasks get` — it PascalCases the payload)
- [ ] Serve locally and pause: human reviews the four states (`?gate=eligibility` / `review` × open / decided)
- [ ] Apply the feedback; pack → `publish -t Action` → deploy the app alone with the shared client id
- [ ] Prove write-back per gateway: fresh claim, complete its task from the CLI, read the record back
- [ ] Update `PROGRESS.md`

- Sidebar — *could this block have run in parallel with the previous one?* In this course we go step by step — we are here to learn, not to race — but in real life independent builds run in parallel, and these two barely overlap: the run block redeploys the solution while this block redeploys the app alone, the contract both depend on was pinned back at registration, and the run block completes its tasks from the command line, never waiting for a screen. Two things to note before overlapping them:
    - **fixtures** — the screens are built against payloads real runs produced, and the first fully populated record exists only once the clean claim has settled; fork there, not at the start of the run block
    - **the write-back proof** — a task decided before a fix proves nothing, so the fresh-task-per-gateway proof joins after the run block is done and the case is stable
