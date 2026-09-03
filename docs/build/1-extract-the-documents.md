# Extract the Documents

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: unlabelled claim forms must come back as typed payloads
- The default route: adopt the shared extraction project and prove it on two claims
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3a · Extraction"
--8<-- "seeds/3a-extraction/prompt.md"
````

- The optional route: build your own extraction project (`3a-extraction/prompt-build.md` in the seed) — when and why
- What to review: keys come from the payload, not from labels; confidence has three states; payload sizes are a design input
- The gate: `check_extraction_keys.py` — every extraction path in the design checked against a real payload
- Proof: a payload beside its form

<!-- Expected agent steps — drafted from the seed prompt; replace/expand from a captured run -->
Steps:

- [ ] Read `contracts/provided-processes.md` (payload shape, field keys) and `CONFIG.md` (the shared IXP project)
- [ ] Generate two claims and run each through the provided Extract Claim Data (IXP) process
- [ ] Read a payload beside its form: six field groups present, damage rows repeating one per item
- [ ] Pin field-key spellings from the live payload; correct `sdd.md` where any binding differs
- [ ] Run the gate: `python3 3a-extraction/check_extraction_keys.py <payload.json>`
- [ ] Record the project name and model version in `PROGRESS.md`
