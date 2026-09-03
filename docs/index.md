# Building Property Insurance Claims automation with Coding Agents

Welcome. In this workshop you build a complete insurance back-office solution — document extraction, a shared claim record, seven decision agents, a long-running case with two human gates, and the screens reviewers decide on. You build it by directing a coding agent, not by writing it yourself.

This is a technical, level-300 exercise. You leave with a working solution in your own folder — and with a process you can reuse: requirements → design → plan → build → verify → hand over, every step checked by something stronger than an opinion.

!!! tip "Training Environment"
    Log in at **[{{ training_url }}]({{ training_url }})** using tenant **{{ training_tenant }}**. Your instructor assigns you a seat — your own folder, where everything you build lives.

## What you'll build

One claim arrives as three PDF documents. A settled claim — or a decision from the right human — comes out. In between:

- an **IXP** extraction that turns the claim form into typed data
- a **Data Fabric** claim record that every component reads and writes
- seven low-code **Agents**, one per family of business rules
- a **Maestro** case orchestrating the whole lifecycle, with two human gates
- a **Coded Action App** — the two screens a reviewer decides on
- a letter recorded for every decision, and a runbook for whoever runs it after you

## The path

1. **[Prepare](prepare/index.md)** — check your tools, learn the workshop rhythm, get the exercise seed.
2. **[Plan](plan/index.md)** — the use case, the requirements document, and the design your agent generates from it.
3. **[Build](build/index.md)** — six blocks. One prompt each, each proven before the next starts.
4. **[Verify](verify/index.md)** — hunt the planted problems, then hand the solution over.

## Key concepts for this course

| Term | Meaning |
|---|---|
| Coding agent | An AI tool in your terminal that reads, writes and executes code autonomously — you direct it in plain English |
| `uip` CLI | The command-line interface the agent uses to talk to the UiPath platform |
| Skills | Packaged instructions that teach a generic coding agent to build on UiPath well |
| The seed | The exercise repository you clone: the requirements, the contracts, and one prompt per block |
| A block | One unit of the build: one prompt in, one proven component out |
| A gate | A check a block must pass before the next one starts — a script or a platform validation |
