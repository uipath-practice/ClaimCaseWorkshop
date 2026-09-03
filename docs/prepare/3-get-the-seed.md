# Get the Seed

The seed is one public repository holding everything the exercise gives you: the requirements, the environment reference, the contracts, and one prompt per block. Every path in it is relative to its root, so the folder you create now is where the whole day happens.

## Clone it

```bash
git clone https://github.com/uipath-practice/PropertyClaimsSeeds.git ClaimCase-<seat>
cd ClaimCase-<seat>
```

Name the folder for your seat. If you cannot use git:

```bash
curl -L https://github.com/uipath-practice/PropertyClaimsSeeds/archive/refs/heads/main.zip -o seed.zip
unzip seed.zip && mv PropertyClaimsSeeds-main ClaimCase-<seat>
```

Prefer the clone. With git, `git status` answers *what did I build* and `git diff` answers *what did I change of theirs* — the difference between writing up your build from evidence and writing it from memory. The `VERSION` file records which seed you have; quote it first in any problem report.

## What's inside

| Path | What it is |
|---|---|
| `README.md` | The front door: the block sequence and how to work it |
| `PDD.md` | The business requirements — the document the whole build answers |
| `CONFIG.md` | The environment reference card: tenant, names, what already exists |
| `PROGRESS.md` | A skeleton your build fills in — the memory between blocks |
| `contracts/` | The pinned interfaces: the claim record schema, the component list, the review-task shape, the provided automations |
| `method/` | The delivery method the blocks follow, and the PDD/SDD guides |
| `known-issues/` | Platform behaviours worth knowing before they cost you an hour |
| `1-design/` … `5-ship/` | One folder per block: `prompt.md`, `cookbook.md`, sometimes a gate script |
| `log-finding.py` | How findings get logged |

A block folder ships a prompt, a cookbook and sometimes a gate. Anything else that appears in it is yours.

## Provided vs. built

The plumbing is provided; you build the thinking.

| Provided — bind, don't build | You build |
|---|---|
| Six deployed automations (generator + document/payload plumbing) | The Data Fabric claim record |
| The shared IXP extraction project, published and pinned | The seven Agents |
| The shared app registration for the review screens | The Maestro case |
| The claim generator (its dials are explained in Verify) | The Coded Action App's two screens |

The instinct on meeting "the policy PDF is in a bucket" is to build a downloader. Don't — whole sessions have been lost that way. If it moves files or payloads, it already exists.

## Two surprises worth meeting now

!!! warning "A solution folder is not the same folder"
    Deploying a solution creates a sub-folder — and it does not inherit its parent's processes or buckets. The resulting failure is the most confusing one in the exercise: a five-second fault naming a process that plainly exists. When you see it, check *which* folder the case is looking in.

!!! info "One click no agent can do"
    You create the Data Fabric connection yourself, and it needs one OAuth consent in a browser. A coding agent can drive almost everything in this exercise — the exceptions are where a human identity must be asserted. Now it's an expected step, not a blocker.

## What you will produce

- `sdd.md` — the design (block 1) — and `tasks.md` — the plan (block 2)
- `Build/ClaimCase-<seat>/` — the solution: the Maestro case and the seven Agents
- `Build/claim-review-<seat>/` — the standalone Coded Action App
- a filled `PROGRESS.md`, your logged findings, and — at the end — the operator runbook

## Pre-flight

- [ ] `uip login status` — right tenant, right folder. Nearly every "not found" today is a wrong tenant, wrong folder, or stale cache — build the habit now
- [ ] `uip --version` — the CLI self-updates, so knowing which version you ran matters later
- [ ] `python3 log-finding.py --identify` — declares your agent, model and CLI version once, so results are diagnosable
- [ ] Open `README.md` in the seed and read "The sequence" — five minutes, and the whole day makes sense
