# Read the PDD

The seed's `PDD.md` is a signed, versioned Process Definition Document — fifteen sections describing how a property claim is handled, written by the business user and business analyst for whoever designs the solution. It is synthetic, but internally consistent and complete: **every figure in it is a real oracle your build will be tested against.**

You have the document in your cloned seed; every **§ link on this page opens the same document on GitHub** at that exact section, so you can jump back and forth without leaving the course.

## Why it names no product

Search it — you will not find an **UiPath Agent**, a **Maestro Case**, a **Data Fabric Entity** or any product name. That is deliberate, and it is what makes block 1 a design exercise rather than a transcription. The **PDD says what the business does** and which decisions need judgement; *your design* decides what becomes an Agent, what becomes an expression, and what is already deployed and merely bound.

The single most load-bearing column in the document is **decision nature** in the step table ([§5.3](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#53-detailed-step-table)): every step is marked *rule-expressible* (the rule can be written down and applied the same way every time) or *judgement* (something is being weighed, and what is weighed is named). That column, more than anything else, drives your architecture.

??? quote "See it in the original — §5.3, Stage 2: five checks, three of them judgement (verbatim)"
    [Open §5.3 in the full document ↗](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#53-detailed-step-table) — rule links inside the excerpt point into the full document.

    --8<-- "seeds/PDD.md:378:389"

## The tour: where the detail lives

| Section | What it holds | You'll need it |
|---|---|---|
| [§1–§2](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#1-purpose-and-business-case) | Purpose, success criteria SC1–SC6, scope, assumptions | Now — it frames everything |
| [§3](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#3-personas-and-responsibilities) | The five personas and what each must be able to see | When the review screens are designed |
| [§4](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#4-as-is-process) | The as-is process and its pain points | Context — what must not be reproduced |
| [**§5.3**](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#53-detailed-step-table) | The step table: every step, its actor, its **decision nature** | Now, and at every design review |
| [§5.4](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#54-control-flow-structure) | Control-flow structure: what forks, what waits, what repeats | The case block |
| [§5.5](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#55-lifecycle-stages-and-slas) | Lifecycle stages and SLAs — and which stages are exceptional | The case block |
| [§5.6](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#56-documents-and-unstructured-input) | The three documents and their structure | The extraction block |
| [**§5.7**](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#57-human-decision-and-approval-points) | The two human touchpoints: who decides, what they must see, what happens if nobody acts | Now, and at the app block |
| [**§7**](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#7-business-rules) | The business rules, BR-01 onwards, grouped by family — eligibility, report validation, coverage, settlement, credibility, decision rules, correspondence, overrides | During the agents block, by rule id |
| [**§7.9**](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#79-what-is-not-a-finding) | *What is not a finding* — the rules that keep clean claims clean | Half the job. Read it twice |
| [§8–§10](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#8-exceptions-and-error-handling) | Exceptions, integrations, compliance controls | Reference |
| [§11](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#11-reporting-and-monitoring-requirements) | Reporting: what the claims team lead must see | The dashboard — a later chapter |
| [§13](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#13-test-data-and-canonical-examples) | One canonical worked example, and the catalogue of what can be planted | [§13.2](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#132-examples-per-rule-and-exception-path) now; [§13.1](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#131-canonical-case--complete) again at verify |
| [§14](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#14-out-of-scope-for-automation) | Out of scope — nothing here may appear in your component inventory | At design review |

## How to read it today

- **Read now:** §1–§2, the [§5.1 narrative](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#51-to-be-narrative) and [§5.2 map](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#52-to-be-process-map), §5.7, §13.2. Twenty minutes, and you know the process.
- **Reference later:** §7 rule by rule during the build — your agent will cite rule ids like `BR-24`; §5.4/§5.5 at the case block; §13.1 at verify.
- **Mind the vocabulary.** The [glossary](https://github.com/uipath-practice/PropertyClaimsSeeds/blob/main/PDD.md#glossary-and-operational-vocabulary) at the top fixes the business's exact words — ***claim***, never *case* or *ticket*; ***assessor report***, never *survey*. Synonym drift in a design turns into wrong stage and outcome names downstream, so the same discipline applies to everything you and your agent write.

??? quote "See it in the original — the glossary and the verbatim labels"
    --8<-- "seeds/PDD.md:63:83"

!!! tip "Documents might disagree sometimes — that's a finding"
    The seed also ships `contracts/` — pinned technical interfaces so that each solutions resides within testable frame specs. If the PDD and a contract ever seem to disagree, the contract wins for anything at a component boundary, and the disagreement is worth logging. You'll meet this again at the design gate.
