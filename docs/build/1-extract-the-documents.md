# Extract the Documents (Block 3a)

The claim form is the one document that arrives as a **structured form**, so it is read into fields with **IXP**. The policy and the assessor report are prose — they stay documents, and the Agents will read them directly. This block proves the reading before anything downstream binds to it.

Nothing is created here. The shared IXP project already exists, published and pinned, and the provided *Extract Claim Data* automation is wired to it. Your job is to adopt it and prove it — the extraction is provided infrastructure, like the generator and the retrieval processes: **bind these, never rebuild them.**

## The prompt

````markdown title="Prompt — block 3a · Extraction"
--8<-- "seeds/3a-extraction/prompt.md"
````

Steps:

- [x] Read `contracts/provided-processes.md` (payload shape, field keys) and `CONFIG.md` (the shared IXP project)
- [x] Generate two claims and run each through the provided Extract Claim Data (IXP) process
- [x] Read a payload beside its form: six field groups present, damage rows repeating one per item
- [x] Pin field-key spellings from the live payload; correct `sdd.md` where any binding differs
- [x] Run the gate: `python3 3a-extraction/check_extraction_keys.py <payload.json>`
- [x] Record the project name and model version in `PROGRESS.md`

Prefer to train your own extraction model instead? `3a-extraction/prompt-build.md` in the seed is the supported second route — same output shape, about an hour of labelling.

## What to review

- **Why two claims.** One claim proves the fields exist; the second proves the key set does not vary and the damage inventory repeats one row per item, not one blob.
- **Keys come from the payload, never from the form's labels.** The model emits `TypeOfIncident`, not the printed *Type of Incident*. Every extraction binding downstream is optional-chained, so a wrong key never throws — it silently yields nothing, and the first symptom would be an empty field three blocks from now. That is exactly why this block ends with a checker.
- **Confidence has three states**, not two: confident, unconfident, and *absent*. A threshold rule that special-cases only one of them ends up flagging empty optional fields as data problems.
- **Payload sizes are a design input.** About 5,000–5,600 characters per claim, ~500 per damage row, five rows maximum — numbers your entity columns and agent input budgets are sized against in the next blocks.

!!! note "Publishing is not deploying"
    The shared model is *published* and callers pin its version — it needs no deployment into your folder at all. Two different verbs, two different lifecycles; keeping them apart will matter again at the app block.

## The gate

```bash
python3 3a-extraction/check_extraction_keys.py <payload.json>
```

It walks **every extraction path your design reads** against a real payload — the one class of defect that fails silently everywhere else.

## Proof

<!-- screenshot: a payload JSON beside its claim form PDF — the damage inventory repeating per row -->

Two claim forms you have never seen come back with every field group populated, the damage rows repeating correctly, and every key your design reads confirmed against a real payload.
