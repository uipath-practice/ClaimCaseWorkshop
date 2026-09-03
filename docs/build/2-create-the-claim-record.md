# Create the Claim Record

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: one claim record every component reads and writes — the pinned entity schema
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3b · Claim record"
--8<-- "seeds/3b-entity/prompt.md"
````

- What to review: the write-semantics trap (omitted preserves, null destroys, empty destroys silently); JSON column budgets; one name in three casings
- Done when: cents survive a round-trip and a 9,000-character payload fits
- Proof: the table and a row in it

<!-- Expected agent steps — drafted from the seed prompt; replace/expand from a captured run -->
Steps:

- [ ] Read `contracts/claim-entity.md` (pinned schema, five column tables, casing rule) and `CONFIG.md`
- [ ] Load the uipath-platform skill (`uip df`); create the entity in the seat folder from a schema file — one create, no read-edit-write repair loop
- [ ] Round-trip: write cents and a 9,000-character payload, read both back unchanged, delete the test row
- [ ] Record the entity name and folder in `PROGRESS.md`
