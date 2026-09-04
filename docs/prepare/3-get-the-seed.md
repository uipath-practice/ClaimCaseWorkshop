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
unzip seed.zip 
mv PropertyClaimsSeeds-main ClaimCase-<seat>
```

Prefer the clone. With git, `git status` answers *what did I build* and `git diff` answers *what did I change* — the difference between writing up your build from evidence and writing it from memory. 

## What's inside

| Path                    | What it is                                                                                                                       |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `README.md`             | The front door: the block sequence and how to work it                                                                            |
| `PDD.md`                | The **business requirements**: the document the whole build works from                                                           |
| `CONFIG.md`             | The **environment** reference card: tenant, names, what already exists                                                           |
| `PROGRESS.md`           | A skeleton your build fills in: **the memory between blocks**                                                                    |
| `contracts/`            | The pinned interfaces: the claim record schema, the component list, the review-task shape, the provided automations              |
| `method/`               | The delivery method the blocks follow, and the PDD/SDD guides. These are templates/reference only and not used during the build. |
| `known-issues/`         | Platform behaviours worth knowing, saves time to your agent.                                                                     |
| `1-design/` … `5-ship/` | One folder per block: `prompt.md`, `cookbook.md`, sometimes a gate script is inside.                                             |
| `log-finding.py`        | How build findings get logged                                                                                                    |

## Provided vs. built

Your Orchestrator seat folder comes with few dependencies: mechanical RPA automations, Storage Buckets, reusable IXP project for claims. Tenant also exposes shared resources. Bind those, don't build your own. This way you will focus on build the thinking part and not basic scripts.

## What you will produce

- `sdd.md` and `tasks.md`: the plan (block 1 & 2)
- `Build/ClaimCase-<seat>/`: Solution: the Maestro Case and the seven Agents
- `Build/claim-review-<seat>/`: the standalone Coded Action App
- a filled `PROGRESS.md`, your logged findings, and at the end the operator's `runbook.md`

## Pre-flight

- [ ] `uip login status` — right tenant, right folder. Nearly every "not found" is a wrong tenant, wrong folder, or stale cache — build the habit now
- [ ] `uip --version` — the CLI self-updates, so knowing which version you ran matters later
- [ ] `python3 log-finding.py --identify` — declares your agent, model and CLI version once, so results are diagnosable
- [ ] Open `README.md` in the seed and read "The sequence" — five minutes, and the whole day makes sense
