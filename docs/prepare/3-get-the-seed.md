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

```text
ClaimCase-Pro % ls -la 
total 352 
drwxr-xr-x@ 26    832    4 Sep 14:17  . 
drwxr-xr-x 9      288    4 Sep 14:16  .. 
drwxr-xr-x@ 3     96     4 Sep 14:17  .claude 
drwxr-xr-x@ 12    384    4 Sep 14:16  .git 
drwxr-xr-x@ 3     96     4 Sep 14:17  .workshop 
drwxr-xr-x@ 5     160    4 Sep 14:16  1-design 
drwxr-xr-x@ 4     128    4 Sep 14:16  2-plan 
drwxr-xr-x@ 7     224    4 Sep 14:16  3a-extraction 
drwxr-xr-x@ 4     128    4 Sep 14:16  3b-entity 
drwxr-xr-x@ 4     128    4 Sep 14:16  3c-agents 
drwxr-xr-x@ 5     160    4 Sep 14:16  3d-case 
drwxr-xr-x@ 4     128    4 Sep 14:16  3e-run 
drwxr-xr-x@ 6     192    4 Sep 14:16  3f-validation 
drwxr-xr-x@ 4     128    4 Sep 14:16  4-verify 
drwxr-xr-x@ 4     128    4 Sep 14:16  5-ship 
-rw-r--r--@ 1     15419  4 Sep 14:16  AGENTS.md 
-rw-r--r--@ 1     225    4 Sep 14:16  CLAUDE.md 
-rw-r--r--@ 1     12449  4 Sep 14:16  CONFIG.md 
drwxr-xr-x@ 6     192    4 Sep 14:16  contracts 
drwxr-xr-x@ 5     160    4 Sep 14:16  known-issues 
-rwxr-xr-x@ 1     23540  4 Sep 14:16  log-finding.py 
drwxr-xr-x@ 7     224    4 Sep 14:16  method 
-rw-r--r--@ 1     98226  4 Sep 14:16  PDD.md 
-rw-r--r--@ 1     1154   4 Sep 14:16  PROGRESS.md 
-rw-r--r--@ 1     9818   4 Sep 14:16  README.md 
-rw-r--r--@ 1     38     4 Sep 14:16  VERSION
```
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
