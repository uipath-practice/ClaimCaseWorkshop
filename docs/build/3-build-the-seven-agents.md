# Build the Seven Agents

<!-- DRAFT STUB — structure approved; content pass pending. Bullets below are the planned content of this page. The prompt below is transcluded live from the seed. -->

Planned content:

- The problem: seven checks, each with a single owner — why seven agents, why low-code, why before the case exists
- The prompt (transcluded from the seed):

````markdown title="Prompt — block 3c · Agents"
--8<-- "seeds/3c-agents/prompt.md"
````

- What to review: a prompt governs what an agent *reports*, not what it concludes; "what is not a finding" is half the job; typed output fields beat paragraphs of prompt
- Done when: each agent returns what the business rules say — **including nothing at all on a clean claim**
- Proof: one agent's trace

Steps:

- [ ] Check `uip login status` and the solution status
- [ ] Read the low-code agent reference files from the skill
- [ ] Build the EligibilityScreening agent (BR-01–BR-05)
- [ ] Build the AssessmentReportValidation agent (BR-06–BR-09)
- [ ] Build the CoverageAnalysis agent (BR-10–BR-16)
- [ ] Build the SettlementCalculation agent (BR-20–BR-29)
- [ ] Build the CredibilityAssessment agent (BR-30–BR-33)
- [ ] Build the DecisionRecommendation agent (BR-40–BR-45, BR-60–BR-62)
- [ ] Build the ClaimantCorrespondence agent (BR-50–BR-52)
- [ ] Test each agent with `uip agent debug`
- [ ] Upload the solution to Studio Web
- [ ] Update `PROGRESS.md`