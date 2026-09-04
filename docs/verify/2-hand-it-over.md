# Hand It Over (Block 5)

Everything runs and block 4 proved it. The last block **deploys nothing** — the deployment you verified is the one that ships. UAT and production are the same package landing in another tenant with that environment's config; that happens in an organization's environments, not in this exercise. What this block does is make the build *transferable*: pin what runs, true up the design, and write for the person who wasn't here.

## The prompt

````markdown title="Prompt — block 5 · Ship"
--8<-- "seeds/5-ship/prompt.md"
````

Steps:

- [x] Pin in `PROGRESS.md`: deployment name, package name + version, both folder keys, the case release key (never the rotating operation Key), the app's deployed version
- [x] Check what travelled: case + seven Agents inside the `.uipx`, app deployed beside it, no hand-deployed stand-ins — a read, not a redeploy
- [x] Bring `sdd.md` to as-built: an As Built section, Design Feedback + Action Required rows for what verify fixed in the case
- [x] Close every task in `tasks.md` (done, or says why not); final solution upload
- [x] Write the operator runbook: prerequisites, deploy and promotion, known-broken with the change each needs, what to do when a claim faults
- [x] Close `PROGRESS.md` with the state of the seat

## What to review

- **Pins, not keys.** A deployment's operation key rotates with every operation; the name, the package name and version, the folder keys and the case release key do not. Pin the stable ones — a runbook full of rotating identifiers is stale before it's read.
- **Check what travelled.** The case and the seven Agents belong inside the `.uipx`; the app is deployed beside it. The thing to catch: something you deployed by hand mid-build silently standing in for a project that never made it into the package. This is a read of the package and the deployments — not a redeploy.
- **Look hardest at what block 4 fixed in the case.** A condition that narrows a rule a business user signed is a **design change**, whether or not anyone wrote it down. It goes into the SDD as a Design Feedback row *and* an Action Required row — first in line to be signed. Where the as-built section and the original design differ, the as-built is right.
- **The runbook is for a different reader.** Not the agent that built the solution, and not you tomorrow — a human operating it who was never here: what has to exist first (the provided processes, the shared IXP project, the entity, the shared connection), how it deploys and would be promoted, what is known-broken, and what to do when a claim faults. Most of the facts already sit in `PROGRESS.md`; this is a rewrite for someone who cannot ask you a question. And a known limitation is written **with the change it needs** — a limitation without one is a complaint.

!!! note "What 'done' means"
    "The build is done" is a statement about a **pinned version**, an **as-built design** and a **runbook** — never about the last green run. Trust in the solution, like trust in an agent, attaches to evidence per decision, not to a good afternoon.

## Proof

<!-- screenshot: Studio Web showing the solution that is running — version matching the pinned one in PROGRESS.md -->

The deployed version is the one you packed; `sdd.md` describes what runs; every task is closed; the runbook exists. Someone you have never met could redeploy this tomorrow.
