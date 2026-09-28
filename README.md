# ClaimCase Workshop

The participant guide for a hands-on workshop: build an enterprise property-claims solution end to end by directing a coding agent on the UiPath platform.

**Read it at [uipath-practice.github.io/ClaimCaseWorkshop](https://uipath-practice.github.io/ClaimCaseWorkshop/).**

One claim arrives as three PDF documents; a settled claim, or a decision from the right person, comes out. On the way you build an IXP extraction, a Data Fabric claim record, seven low-code Agents, a Maestro case with two human gates, a Coded Action App for the reviewers and a Coded Web App for the claims team lead. The audience is technical (level 300), and participants bring the coding agent they already use.

## The path

| Section | What happens |
|---|---|
| **Prepare** | Check the tools, learn how a block runs, get the exercise seed |
| **Plan** | Read the business requirements (PDD); the agent generates the solution design (SDD) and the task list |
| **Build** | Six blocks, one prompt each, each proven by a gate before the next starts |
| **Verify** | Hunt planted problems in generated claims, then hand the solution over |
| **App** | Build the process app: the portfolio view over every claim |
| **Next Steps** | What transfers to your own process, and the references the course quotes |

## How this repo works

- **Site:** MkDocs Material. Pages live in `docs/`, one folder per section, and the navigation is in `mkdocs.yml`.
- **The seed** is its own repository, [PropertyClaimsSeeds](https://github.com/uipath-practice/PropertyClaimsSeeds), mounted here as the `seeds/` submodule. Lesson pages transclude its prompts at build time (`pymdownx.snippets`), so the course always shows the exact prompt a participant runs. The pinned submodule commit is the seed version a cohort uses; `seeds/VERSION` names it.
- **Seed excerpts by line range** (`--8<-- "seeds/PDD.md:380:391"`) do not fail the build when the seed moves; they render the wrong lines. After every `seeds/` bump, re-check them (`CLAUDE.md`, rule 3).
- **Environment values** (training URL, tenant) are macros from `main.py`, switched with `COURSE_ENV` (`staging` or `prod`).
- **Authoring rules and templates** live in `Master/`, and `CLAUDE.md` carries the always-on subset for coding agents. `Master/Language.md` covers voice, word choices and the patterns that make a page read as generated.
- **Maintainer commands** for Claude Code (new, review and publish a lesson or exercise) are in `.claude/commands/`.
- **Localization** is wired (`mkdocs-static-i18n`) but dormant: English only for now.

## Preview locally

```bash
git clone --recurse-submodules https://github.com/uipath-practice/ClaimCaseWorkshop.git
cd ClaimCaseWorkshop
pip install -r requirements.txt
mkdocs serve                 # http://127.0.0.1:8000
mkdocs build --strict        # run before every commit; a missing include fails it
```

In an existing clone, `git submodule update --init` fetches the seed. Draft pages stay out of `mkdocs.yml`; a maintainer previews them with a local, untracked `mkdocs.local.yml`.

## Deploy

Every push to `main` runs `.github/workflows/deploy.yml`, which builds with `COURSE_ENV=prod` and publishes to the `gh-pages` branch, so a push to `main` goes live.

## Feedback

Found something broken, unclear or out of date? [Open an issue](https://github.com/uipath-practice/ClaimCaseWorkshop/issues), or tell your instructor.
