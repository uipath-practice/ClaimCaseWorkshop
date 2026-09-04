# Create the Claim Record (Block 3b)

The PDD asks for a store that outlives any single step and can be read while the claim is in flight. That is a **Data Fabric** entity, and this block builds it — one entity, in your seat folder, on the pinned schema from `contracts/claim-entity.md`.

The schema is pinned for a reason worth reading in the contract itself: every seat builds a compatible record, so one reference screen can read any seat's claim and every seat's letters compare. 

## The prompt

````markdown title="Prompt — block 3b · Claim record"
--8<-- "seeds/3b-entity/prompt.md"
````

Steps:

- [x] Read `contracts/claim-entity.md` (pinned schema, five column tables, casing rule) and `CONFIG.md`
- [x] Load the uipath-platform skill (`uip df`); 
- [x] Create the entity in the seat folder
- [x] Round-trip: write cents and a 9,000-character payload, read both back unchanged, delete the test row
- [x] Record the entity name and folder GUID in `PROGRESS.md`

## What agent will review

- **One create, from a file.** Update takes a different body shape from the one `get` returns, so the natural read-edit-write loop does not work here. Creating fresh from a schema file is one call and no repair.
- **Two budgets, and they are not the same number.** JSON columns hold 10,000 characters, and every producer budgets 8,000 in its prompt — headroom is the contract. Separately, every *consumer's* summed inputs must stay under the platform's cap on serialized arguments. Your SDD already states both as arithmetic; this is where the numbers become real.
- **The connection is shared, and that's deliberate.** Authorizing a Data Fabric connection is an interactive OAuth consent. One shared connection serves every seat.

## The gate

The round-trip *is* the gate: a value with cents and a 9,000-character payload written, read back unchanged, and the test row deleted. Round-trip before you build on it — a store you have only written to is a store you know half of.

## Proof

<!-- screenshot: the entity's column list in Data Fabric, and one row with a JSON payload column populated -->

The table exists in your seat folder on the pinned schema, and a real row survived the round-trip.
