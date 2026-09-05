# Hunt the Planted Problems (Block 4)

The PDD's §13.2 lists what can be wrong with a claim; §1.3 says what success means numerically. This block establishes both — and expect to spend most of it **fixing and fine tuning rather than measuring**. 

## The prompt

````markdown title="Prompt — block 4 · Verify"
--8<-- "seeds/4-verify/prompt.md"
````

Steps:

- [x] Run **three clean claims** first — all settle in full, no task ever raised
- [x] Read the answer key by probe: one standalone generator call per injector id
- [x] Aim **one run per planted problem**: matching fail scenario + pinned discrepancy id
- [x] Confirm the pin landed before treating the run as evidence
- [x] **Record per problem**: which Agent caught it, which gate task showed it
- [x] **Fix** at the source **re-run** the batch **after every fix that tightens a rule**
- [x] **Reproducibility check**: two clean claims with one `profileId` settle to the same cent
- [x] **Conformance sweep** of `sdd.md`: Implemented · Missing · Mismatch · Extra
- [x] Update `PROGRESS.md`

## Clean claims first

A pinned run proves **detection**; a clean run proves **restraint** — and restraint is the harder half. Three clean claims settle untouched before any problem is chased, and the clean batch re-runs **after every fix that tightens a rule**: over-flagging is the failure that reappears, and one aimed run cannot see the cost of a fix. 

## Aiming a run

The generator takes four dials, and this is where they matter:

| Dial | What it does |
|---|---|
| `scenario` | Aims the claim broadly — `auto-settle`, `eligibility-fail`, `review-fail`, `both-fail`, `random` |
| `discrepancy` | Pins **one exact injector id** — the only way to guarantee a problem is present |
| `profileId` | Repeats a claimant (`claims-profile-01`…`12`) — the reproducibility tool |
| `seed` | Makes the documents themselves identical between runs |

A scenario does not guarantee a route; a pinned id does — and `auto-settle` *suppresses* a pin entirely, so aim with the matching fail scenario plus the exact id. The generator's own fault message on an unknown id lists the valid ones. Then read the claim's own answer key to confirm the pin landed **before** treating the run as evidence.

## Read the key by probe

Once sanctioned, the cheapest authoritative read is one standalone generator call per injector id — seconds each, no case instance, no Agent spend. That yields the full *injector → owning check → gate → letter wording* map before any campaign run. Read it as a record of what was **injected**, never of what the arithmetic must produce: a planted problem your rules correctly neutralize reads as a miss and is the build being right; a failure no injector plants is a false positive by construction.

## What to establish

- **Each problem caught by the Agent that owns it**, stopping the claim at the right gate — not caught by something else, and not caught twice. One problem reported by three Agents reads to a reviewer as three problems.
- **What the claimant is told matches what happened.** Read the letter from the correspondence entity, never the job log — and read the paid figure from `decisionJson.outcome` against `status`, never from `settlementJson`: that column holds what the settlement *computed*, and after an override the confirmed figures live elsewhere.
- **Two clean claims of one profile settle to the same cent.** Same `profileId`, compare every figure of both records, never the prose. Same `seed` too makes the documents identical — which is what separates agent variance from document variance. This is where temperature 0 pays its bill.
- **Fix at the source, in the block that owns it.** And mind the reach of a fix: a case-plan change reaches only instances started *after* the redeploy; an agent change reaches the next call on any instance. Bump, deploy, then start the batch — never deploy into a running one and read half the change.

Verifying a claim, as *The Work That Remains* puts it, has two parts: deciding what the checkable pieces are, and checking them — and "the breakdown fails silently… the mistake is not inside any piece; it lives in how the problem was split into pieces." Your results table is that breakdown, made visible and scored.

## The conformance sweep

Then check the build against the **design**, not just the process: enumerate every stage, task, rule, SLA and variable in `sdd.md` and mark each **Implemented · Missing · Mismatch · Extra**. *Extra* deserves the hardest look — it is what nobody asked for, no tool reports, and every reviewer pays for later.

## Proof

Evidence from a real run of this block — the aimed campaign, one row per planted problem:

??? example "The results table — nine injectors against the answer key (expand)"

    | Injector | Owner per the key | Caught by | Gate |
    |---|---|---|---|
    | ELIG_POLICY_LAPSED (BR-01) | EligibilityScreening | ✓ BR-01 policy status | H1 → Refuse |
    | ELIG_IDENTITY_MISMATCH (BR-02) | EligibilityScreening | ✓ BR-02 identity | H1 → Refuse |
    | ELIG_ADDRESS_MISMATCH (BR-03) | EligibilityScreening | ✓ BR-03 address | H1 → Refuse |
    | ELIG_COVERAGE_PERIOD (BR-04) | EligibilityScreening | ✓ BR-04 coverage period | H1 → Refuse |
    | ELIG_LATE_FILING (BR-05) | EligibilityScreening | ✓ BR-05 filing deadline | H1 → Refuse |
    | REVIEW_CAUSE_MISMATCH (BR-15) | CoverageAnalysis | ✓ BR-15 peril classification | H2 → Approve |
    | REVIEW_NARRATIVE_CONTRADICTION (BR-30) | CredibilityAssessment | AssessmentReportValidation — BR-08 *(see below)* | H2 → Approve |
    | REVIEW_PRIOR_CLAIM_EROSION (BR-24) | SettlementCalculation | ✓ BR-24 aggregate bound, remainder quoted | H2 → Approve |
    | REVIEW_AMOUNT_INFLATION (BR-29/41) | SettlementCalculation | ✓ BR-29 ratio 1.2575 | H2 → Approve |

    All nine reached a human — zero reached no gate task.

**The ninth row is the exercise working, not failing.** The key names CredibilityAssessment (BR-30) as owner — but the injector wrote the contradiction into the *assessor report*, and BR-30 is explicitly about the claimant's *own account*. AssessmentReportValidation caught it under BR-08, quoting both statements; CredibilityAssessment abstained and said why. The claim stopped at the right gate with the right evidence — detection met on substance — and the owner-label disagreement between the key and the PDD was **logged as a finding rather than silently absorbed**. When two authorities disagree, that is the finding.

**Restraint, measured.** The canonical clean claim settled untouched five times for five, to the cent — two of those runs on *identical documents* (same profile, same seed), every figure matching: the reproducibility test passed on agent variance alone. Two clean claims escalated *correctly* — their assessor reports never became usable, and a claim with no independent assessment is not a claim with nothing wrong. And two were falsely escalated, both on one profile, both by a judgement check inventing a conflict its own evidence contradicts — so the false-escalation target was **honestly missed**. The line that run drew is worth keeping: **derive what you can compute** — every arithmetic check moved into a case condition never over- or under-fired again — and accept that what remains judgement will occasionally cost a human review.

And the run's own checkers, written during this block, closing it out:

```console
$ python3 4-verify/check_letters.py
256 check(s), 0 failure(s), 19 skipped
WHAT THE CLAIMANT WAS TOLD MATCHES WHAT HAPPENED, on every claim checked
$ python3 4-verify/check_conformance.py
434 checks: 434 Implemented, 0 Missing, 0 Mismatch, 0 Extra
```

Per problem: which Agent caught it and which task showed it to a human. And every clean claim in, settled, untouched.
