# Build the Review Screens (Block 3f)

Everything so far runs invisibly. This block builds the only part of your solution anyone will ever *see*: the **Coded Action App**'s two screens — the eligibility review and the claim review — that the **Maestro** case raises its tasks against in **Action Center**.

Screens come last for a reason: by now your own runs have populated real records, so the screens are built against **payloads your own Agents actually produced**, not against payloads you imagined. Capture fixtures from your Data Fabric records — never invent them, and never capture from `uip tasks get`, which PascalCases the whole payload for display.

## Decided for you, and not

- **What each reviewer must see** — `PDD.md` §5.7, and it says *not a summary*: the stages, every check including the passes, the settlement line by line, the three documents, two outcomes with a written reason.
- **The layout** — `3f-validation/layout.md` fixes the regions of both screens, so every seat's screen is reviewable against one expectation.
- **The look** — `3f-validation/brand.md` carries the palette, type and CSS tokens.
- **The rest is yours** — and worth stating to your agent explicitly. Asked for "a screen that shows a claim," an agent produces a correct form generated from a schema. **Taste is a requirement you have to state**: what is visible before scrolling, what opens on demand, how the width is used. Everything else in a spec is checkable; this one it will silently skip.

## The prompt

````markdown title="Prompt — block 3f · Action App"
--8<-- "seeds/3f-validation/prompt.md"
````

Steps:

- [x] Read `PDD.md` §5.7, `contracts/review-task.md`, `3f-validation/layout.md` and `brand.md`
- [x] Load the uipath-coded-apps skill; replace the registered app's empty page with the two gate screens
- [x] Capture fixtures from your own Data Fabric records (never from `uip tasks get` — it PascalCases the payload)
- [x] Serve locally and pause: human reviews the four states (`?gate=eligibility` / `review` × open / decided)
- [x] Apply the feedback; pack → `publish -t Action` → deploy the app alone with the shared client id
- [x] Prove write-back per gateway: fresh claim, complete its task from the CLI, read the record back
- [x] Update `PROGRESS.md`

## The localhost review — pause here

Every screen fix after a deploy costs a pack → publish → deploy cycle; the same fix on a localhost preview costs a refresh. So the app pauses **before its first publish**, served locally on your captured fixtures, and you review four states:

| Open | What to check |
|---|---|
| `http://127.0.0.1:<port>/?gate=eligibility` | All five checks visible with results and reasons — passes included; the claim recognizable |
| `…?gate=eligibility&state=decided` | A decided task still identifies its claim and shows the decision that survived |
| `…?gate=review` | Every finding side by side, the recommendation with its reasons, the settlement line by line, the documents |
| `…?gate=review&state=decided` | The confirmed figures — carrying a real settlement override, not just the recommendation |

Hand what you find back to the agent, let it fix, refresh, and approve — **then** it publishes once. Your iteration loop has layers: a label or layout change needs only a reload; a data change needs new fixtures; only a code change needs the redeploy. Iterate on the cheapest layer that shows the truth — and never let the cheap loop be the last thing you ran.

## What to review

- **A decision carries a reason, always.** The contract makes `reviewerNotes` required at both gates — because an inspected decision with a reason teaches the system which pattern failed; "a rubber-stamped click is theater" (*The Work That Remains*). If the screen makes the reason easy to skip, it built the wrong habit.
- **One malformed field must not take down the screen.** Generated data varies — a field arrives as an object where a string stood on every claim before. Pin shapes upstream where you can, and put a boundary around each panel so a white page becomes one panel saying *"could not render the policy"* with the decision still makeable. Then test on **more than one record** — iterating against a single good example measures how well you handle that example.
- **What survives task completion.** Completing a task drops its inputs; only inOuts and outputs survive — and anything that writes task data *replaces* the payload. Read the current payload, spread it, then write, at every call site. The contract walks through all of it.

## The gate

Your reviewer approving all four localhost states is the first gate. After the one publish, the write-back proof is the second: **a fresh claim per gateway**, its task completed from the CLI, the decision read back from the record — a task decided before a fix proves nothing, so always prove against a fresh one. Clicking through the deployed screens in Action Center is your own optional third check.

## Proof

<!-- screenshot: the claim review screen in Action Center — findings side by side, settlement lines, the two outcome buttons -->

Both gates render in a browser on real data, and a decision — with its reason — lands on the claim record and moves the case on.

---

*Sidebar — could this block have run in parallel with the previous one?* In this course we go step by step — we're here to learn, not to race — but in real life independent builds run in parallel, and these two barely overlap: the run block redeploys the solution while this block redeploys **the app alone**, the contract both depend on was pinned back at registration, and the run block completes its tasks from the command line, never waiting for a screen. Two things to note before overlapping them:

- **fixtures** — the screens are built against payloads real runs produced, and the first fully populated record exists only once the clean claim has settled; fork there, not at the start of the run block
- **the write-back proof** — a task decided before a fix proves nothing, so the fresh-task-per-gateway proof joins after the run block is done and the case is stable
