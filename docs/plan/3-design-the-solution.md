# Design the Solution

Block 1. Your agent reads the PDD and generates the Solution Design Document — one file, `sdd.md`, at a fixed name at the seed root. Everything downstream binds to it: the plan derives from it, the build follows it, verify checks against it, and handover brings it to as-built. It has to be good enough that a solution architect could hand it to a developer and walk away.

## Before you run: the brief is the skill

The planner normally asks its questions before designing — execution mode, delivery model, what components exist, what app type. Watch what happens instead: **it asks nothing.** Every answer is already in what it reads — the mode in the prompt, the tenant from your login, the component inventory in `contracts/components.md`. That is the first lesson of this workshop worth taking home: *the way to a quiet, autonomous agent is a complete brief, not a longer conversation.*

## The prompt

Copy it into your coding agent, started in the seed folder:

````markdown title="Prompt — block 1 · Design"
--8<-- "seeds/1-design/prompt.md"
````

Note the boundary it sets: **design only, then stop.** The task list comes in the next block. One document answers one question; a design that also explains the build order becomes two documents describing the same thing, and the copy nobody edits is the one that goes stale.

Steps:

- [ ] Read `PDD.md`, `CONFIG.md` and `contracts/` (components, claim entity, review task, provided processes)
- [ ] Load the uipath-planner skill; run autonomous, design only
- [ ] Write `sdd.md` at the seed root, with `Tasks file: tasks.md` in the handoff header
- [ ] Add the two sdd-addendum sections (entity write-ownership matrix; design feedback to PDD)
- [ ] Run the gate: `python3 1-design/check_sdd.py sdd.md --pdd PDD.md` — fix findings, rerun until clean
- [ ] Update `PROGRESS.md`

## Review the design

The agent finishes in minutes; your review is where the value is. Four things to check by hand:

- **Every step, its nature respected.** Walk the PDD's §5.3 table against the design: judgement steps became Agents, rule-expressible steps became expressions or deterministic tasks. Each design task should name the PDD step it implements.
- **Where two sections state the same fact, do they agree?** A long generated document is written section by section, and consistency between distant sections is exactly what a sequential writer is worst at. Find the pairs — a field listed in two tables, an owner named twice — and compare them. That is where design defects live.
- **Budgets as numbers.** Every agent's summed inputs against the platform's cap, stated arithmetically — not "should fit".
- **Disagreements resolved out loud.** Where a contract and the PDD pull differently, the design follows the contract *and says so* in its Design Feedback section. A silent resolution is invisible and therefore uncheckable.

## The gate

```bash
python3 1-design/check_sdd.py sdd.md --pdd PDD.md
```

One command, two different checks. The planner's own audit verifies the document's *shape* — sections present, tables well-formed. The cross-check verifies it against the *process*: task types match the PDD's decision-nature column, one writer per data column, every variable that is read is produced by something, argument names are real. Run both, trust neither alone.

This gate is also what makes the exercise model-proof: different models design differently, and a weaker one will occasionally put arithmetic where judgement belongs — silently. The gate catches that on any model, which is why the answer to design variance is a check downstream, never a thicker requirements document.

If a rule fires on something you believe is right — say so and leave the document alone. A wrong rule is a valuable finding; a file edited to satisfy it is worthless.

## Proof

<!-- screenshot: sdd.md open — the stage list and one task with its Design Rationale naming a PDD step; plus the gate exiting 0 -->

A design the checker passes and an architect could hand over: every stage, task, rule and human decision described well enough to build from, with nothing left to guess.
