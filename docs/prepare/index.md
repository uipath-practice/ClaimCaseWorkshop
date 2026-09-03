# Prepare

You are about to build an enterprise-grade claims solution in a day, with a coding agent doing the heavy lifting. This section clears everything that would otherwise compete for your attention once the build starts.

## The exercise at a glance

An insurance company receives property claims — a claim form, a policy, an assessor's report. Today a team screens them, validates the assessment, calculates settlements and writes to claimants: slowly, and a little differently every time. You automate the whole path. A claim with nothing wrong settles untouched; a claim with a problem stops in front of the right person, with everything they need on one screen.

You direct, the agent builds, and a gate checks every block. The goal is not this particular solution — it is leaving able to build the next one, on your own process, at your own company.

## Audience

Technical, level 300. You should be comfortable in a terminal and have driven a coding agent at least once before. UiPath product experience helps but is not assumed — each product is explained when the build reaches it.

## Coding agents

Bring the agent you already use — as the official guidance puts it, "the right choice is usually the agent you already use day to day" ([choosing your agent](https://docs.uipath.com/coding-agents/standalone/latest/user-guide/choosing-your-agent)).

| Agent | Status in this workshop |
|---|---|
| **Claude Code** | Tested — the workshop prompts are proven with it |
| **Codex** | Tested — proven with the same prompts |
| **OpenCode** | Tested — proven with the same prompts |
| Other supported agents | Expected to work; not tested against these prompts |

Where a step differs between agents, the page shows one tab per agent.

## Your seat

A seat is your own folder in the training tenant. It arrives with the shared infrastructure already in place — you never build any of this:

| Already there | What it does |
|---|---|
| Six deployed automations | A claim generator, plus the plumbing that moves documents and payloads |
| A shared **IXP** project | The document-extraction model, published and pinned |
| A shared app registration | The identity your review screens will sign in through |

What you build on top: the claim record, the seven Agents, the Maestro case, and the Action App.

## Prerequisites

- [ ] A laptop you have admin rights on
- [ ] Node.js LTS and `npm`
- [ ] Python 3 (the gate scripts run on it)
- [ ] `git`
- [ ] A coding agent installed and signed in (one of the tested three, or your own)
- [ ] An account on the training tenant — **{{ training_tenant }}** at [{{ training_url }}]({{ training_url }})

## In this section

| Step | What it covers |
|---|---|
| [1. Prepare Your Tools](1-prepare-your-tools.md) | Check the `uip` CLI, sign-in and skills; install what's missing |
| [2. How the Workshop Runs](2-how-the-workshop-runs.md) | The rhythm you'll follow all day: blocks, gates, context, findings |
| [3. Get the Seed](3-get-the-seed.md) | Clone the exercise, see what's inside, run the pre-flight checks |
