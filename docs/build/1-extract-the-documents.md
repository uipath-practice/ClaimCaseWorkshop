# Extract the Documents

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: unlabelled claim forms must come back as typed payloads
- The default route: adopt the shared extraction project and prove it on two claims
- The prompt (transcluded from the seed):

```text title="Prompt — block 3a · Extraction"
--8<-- "seeds/3a-extraction/prompt.md"
```

- The optional route: build your own extraction project (`3a-extraction/prompt-build.md` in the seed) — when and why
- What to review: keys come from the payload, not from labels; confidence has three states; payload sizes are a design input
- The gate: `check_extraction_keys.py` — every extraction path in the design checked against a real payload
- Proof: a payload beside its form
