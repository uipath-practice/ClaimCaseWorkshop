# Prepare Your Tools

<!-- Adapted from CodingAgentsCourse getting-started/1-install-the-cli-and-skills.md — reframed as a check-first refresher. Final wording lands in the content pass. -->

!!! tip "Here is our plan for this lesson:"

    1. Check what you already have — CLI, sign-in, skills.
    2. Install whatever is missing.
    3. Verify that your agent recognizes UiPath tasks.

## Goal

A working setup before the exercise starts: the `uip` CLI installed and authenticated, the UiPath skills added to your coding agent, and a quick check that proves the agent knows how to build with UiPath. If you have done a UiPath coding-agents workshop before, this page is a five-minute checkup.

## Why a coding agent changes how you build

A coding agent already knows how to write code. What it doesn't know is UiPath — your CLI commands, project structures, and platform conventions. Two pieces fix that:

- **UiPath CLI** is the interface the agent uses to talk to the platform. A command-line interface turned out to be the most token-efficient way to expose UiPath to an agent.
- **Skills** are how you teach the agent to use that CLI well. They encode the *sequence* of commands for a task, so you can ask for an outcome instead of memorizing commands.

## Steps

### 1. Check what you have

```bash
uip --version
uip login status
uip skills list
```

If all three answer sensibly, skip to step 5. Otherwise, do only the steps you're missing.

### 2. Install the UiPath CLI

Install the CLI globally. This gives you the `uip` command.

```bash
npm install -g @uipath/cli
```

### 3. Sign in

Authenticate once. Your coding agent reuses this same session, so it acts as you on the platform.

```bash
uip login
```

### 4. Install the UiPath skills

`uip skills install` launches an interactive installer where you pick your agent:

```bash
uip skills install --agent claude
```

The installer walks you through selecting skill bundles. Pick the bundles this workshop uses — the exact list is in the seed's `CONFIG.md`.

!!! info "Good to know"
    The skills registry is public, so this step needs no login. You also don't need to install platform tools first — your agent auto-installs them on first use. **Claude Code** is global-only for skills; the `--local` flag is for other agents like Cursor.

A few commands to keep handy:

```bash
uip login status
uip --version
uip tools update
uip skills update
```

`uip --help` and `uip <command> --help` are your best friends, right after your coding agent.

### 5. Verify the setup

Run your agent with the skills installed and ask it for an outcome — not a command:

```text
which uipath skills I can use? can you list tenants within environments I'm connected to?
```

[[[
A correctly set-up agent will use the tools and give you the answer. If it doesn't recognize UiPath tasks, restart your coding agent once so it reloads plugins.
|30|
![A coding agent proposing the uip command sequence after a plain-language request](1-prepare-your-tools.images/verify-agent-proposes-commands.png){ .screenshot }
]]]

!!! info "Sessions, identity, and security"
    The agent inherits your session and acts with your permissions. For a shared or service identity, sign in with an External Application session instead of a personal login.

    Some agents run commands in isolated environments. In that case, they may not be able to run `uip` with your privileges. If `uip login status` shows you're connected in your terminal but your agent says otherwise, tell it:

    ```text
    When using the UiPath CLI, prefer escalated execution because sandboxed commands may not reflect my real terminal session
    ```

    Avoid approving a blanket **uip** rule — that also covers destructive commands. Better to approve read/list prefixes as they come up.

Done. Your tools are ready.
