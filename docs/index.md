# Building Property Insurance Claims automation with Coding Agents

Welcome! 

- Companies around the world are increasingly looking to UiPath not just to automate individual tasks, but to orchestrate complex, long-running, and exception-heavy business processes and help drive their AI transformation. 

- **In this workshop you build a complete insurance back-office solution**: document extraction, a claim record in Data Fabric, seven agents that each analyze the claim from a different angle, a long-running case with two human gates, and the validation app reviewers use to make decisions. 

- **Coding agents are now the primary user persona for the UiPath platform.** They enable customers to discover, design, build and operate end-to-end agentic orchestration and automation at enterprise scale. You build the solution by directing a coding agent, not by writing everything yourself. You leave with a working solution in your own folder and a process you can reuse: requirements → design → plan → build → verify → hand over.


## What you'll build

One claim arrives as three PDF documents. What comes out is a settled claim, or a decision from the right human. In between:

- an **IXP** extraction that turns the claim form into typed data
- a **Data Fabric** claim record that every component reads and writes
- seven **low-code Agents**, one per family of business rules
- a **Maestro** case orchestrating the whole lifecycle, with two human gates
- a **Coded Action App** with the two screens a reviewer decides on
- a **claimant letter** recorded for every decision, and a **runbook** for whoever runs it after you
- a **Coded Web App**: the portfolio view the claims team lead has never had, with every claim, its stage and its deadline

!!! tip "Training Environment"
    Log in at **[{{ training_url }}]({{ training_url }})** using tenant **{{ training_tenant }}**. Your instructor will invite you and assign you a seat, your own folder where everything you build lives.
## The path

1. **[Prepare](prepare/index.md)**: check your tools, learn the workshop rhythm, get the exercise seed.
2. **[Plan](plan/index.md)**: the use case, the requirements document, and the design your agent generates from it.
3. **[Build](build/index.md)**: six blocks, one prompt each, each proven before the next starts.
4. **[Verify](verify/index.md)**: hunt the planted problems, then hand the solution over.
5. **[App](app/index.md)**: build the process app, the portfolio view over everything you ran.


## Key concepts for this course

| Term          | Meaning                                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------------------- |
| Coding agent  | An AI tool in your terminal that reads, writes and executes code autonomously; you direct it in plain English |
| UiPath CLI    | The command-line interface the agent uses to talk to the UiPath platform                                       |
| UiPath Skills | Packaged instructions that teach a generic coding agent to build on UiPath platform components                 |
| **Seed**      | The exercise repository you clone: the requirements, the contracts, and prompts that instruct coding agents    |
| **Block**     | One unit of the build: one prompt in, one proven component out                                                 |
| **Gate**      | A check a block must pass before the next one starts, usually a script or a platform validation                |
