# Build the Seven Agents (Block 3c)

Seven checks in the process need judgement and it's seven because they are controlled by various departments and business owners. Requirement. **Seven low-code Agents, one per family of business rules**, named in `contracts/components.md`. Nothing else is built here — the deterministic work is already deployed as the provided processes, or belongs in the downstream case as an expression.

Why low-code, and why before the case: the exercise is about a process that uses judgement where the business needs it, not about agent frameworks — and Agents are the only component testable in isolation, so building them first means the case block gets one authoring pass against things that already exist and answer.

## The prompt

````markdown title="Prompt — block 3c · Agents"
--8<-- "seeds/3c-agents/prompt.md"
````

Steps:

- [x] Check `uip login status` and the solution status
- [x] Read the low-code agent reference files from the skill
- [x] Build the **EligibilityScreening** agent (BR-01–BR-05)
- [x] Build the **AssessmentReportValidation** agent (BR-06–BR-09)
- [x] Build the **CoverageAnalysis** agent (BR-10–BR-16)
- [x] Build the **SettlementCalculation** agent (BR-20–BR-29)
- [x] Build the **CredibilityAssessment** agent (BR-30–BR-33)
- [x] Build the **DecisionRecommendation** agent (BR-40–BR-45, BR-60–BR-62)
- [x] Build the **ClaimantCorrespondence** agent (BR-50–BR-52)
- [x] Test each agent with `uip agent debug`
- [x] Upload the solution to Studio Web
- [x] Update `PROGRESS.md`

## What agent will review

- **A prompt governs what an agent *reports*, never what it concludes.** Whether a claim reaches a human is a **case condition** over the outputs these Agents emit (a flag count, a risk level, a net payable) never a sentence in a prompt. 
- **A typed output field beats a paragraph of prompt.** When a payload must contain a fact, we declare it as a field in the output schema. A model fills a declared field reliably; prose asking it to be careful competes with every other sentence.
- **One concern, one owner.** An Agent may cite another's finding as evidence; it may never re-raise it as its own. The reviewer sees every finding at once, and one problem reported by three Agents reads as three problems.
- **PDF documents reach an Agent as job attachments, never as extracted text.** A policy's meaning lives in clause wording that flattening loses. Agents carry the built-in document reader for exactly this reason. 

## The gate

One real invocation per Agent, on a real claim — `uip agent debug` — checking it returns what its §7 section says, **including nothing at all on a clean claim**. A grader's score is about structure and wording; only a run answers whether the agent does the thing.

We don't write agent's evaluations tests here, but it's a good idea; specific input claim + payload, results in a specific expected output. Coding agents do it for us here: we will do end-to-end verification later in this workshop, which will directly evaluate every agents's work as part of the claim processing (with planted issues).

## Proof

<!-- screenshot: one agent's trace — the typed output fields populated, on a real claim -->

Each of the seven runs on a real claim and answers per its rules; the solution is uploaded, and all seven open in **Studio Web**.
