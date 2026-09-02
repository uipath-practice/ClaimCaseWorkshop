# CLAUDE.md — ClaimCase Workshop Site

This file is read automatically on every Claude Code session in this project.
Apply all rules below to every task involving this site — no reminders needed.

---

## Project Purpose

A GitHub Pages–hosted MkDocs site guiding participants through building an
enterprise property-claims solution end-to-end with coding agents (level ~300,
technical audience). One exercise, one site: Prepare → Plan → Build → Verify.

**Live site:** https://uipath-practice.github.io/ClaimCaseWorkshop/ (Pages not enabled until the first content pass)
**Source repo:** https://github.com/uipath-practice/ClaimCaseWorkshop
**Seed (submodule `seeds/`):** https://github.com/uipath-practice/PropertyClaimsSeeds
**Theme:** MkDocs Material (`mkdocs.yml`)
**Deploy:** GitHub Actions on every push to `main` (`.github/workflows/deploy.yml`)

---

## Workshop-Specific Rules (locked)

1. **No assumed coding agent.** Agent-specific steps always go in content tabs
   (`pymdownx.tabbed`) — one tab per agent. Never write a page that only works
   for one agent.
2. **A lesson includes a prompt, never pastes it.** Seed prompts are transcluded
   at build time from the `seeds/` submodule via `pymdownx.snippets` inside a
   **four-backtick** `markdown` fence:

   `````markdown
   ````markdown title="Prompt — block 1 · Design"
   --8<-- "seeds/1-design/prompt.md"
   ````
   `````

   Four backticks because the prompts contain three-backtick code blocks of
   their own — a three-backtick outer fence is terminated by the first inner
   one. The `markdown` language makes Pygments tag the prompt's emphasis and
   headings, which `extra.css` styles bold/italic, so the raw prompt reads
   with its emphasis intact while the copy button copies the exact raw text.
   Never render a prompt as page markdown — what participants copy must be
   byte-for-byte what the seed ships.

   Solution-truth (schemas, names, contracts, commands) is cited from `seeds/`,
   never restated in a page. If a page needs a fact the seed holds, link or
   transclude it.
3. **The pinned submodule SHA is the frozen seed version for a cohort.**
   Bumping `seeds/` is a deliberate act, done between cohorts — never as a side
   effect of a content edit.
4. **Environment values are macros.** `{{ training_url }}`, `{{ training_tenant }}`,
   `{{ env_label }}` — defined in `main.py`, switched with `COURSE_ENV`
   (staging | prod). Never hardcode a URL or tenant in a page.
5. **Diagrams and bullets over prose.** This is a technical workshop — no long
   texts anywhere. Typical page arc: the problem → how we solve it → steps /
   prompt / screenshots → the proof it worked.
6. **One fact, one home.** Nothing is repeated across pages; concepts expand
   gradually in participant order.
7. **No internal kitchen.** This repo is public. No seat names, run counts,
   findings, maintainer tooling, or links to private repos in any page.
8. **English only for now.** Localization machinery is wired (`mkdocs-static-i18n`,
   `Master/Localization.md`, `scripts/translation_status.py`) but no page or
   prompt is translated until international classes are scheduled.
9. **Content passes use the private source material.** The per-block rationale
   drafts and the vocabulary source book are maintained outside this repo; read
   them before writing a section's content. Never commit them here.

---

## Master Reference Files

All framework rules, templates, and formatting conventions live in `Master/`.
Read the relevant file before creating or reviewing content:

| File | What it covers |
|------|---------------|
| `Master/README.md` | Entry point — what each file contains, sanity rules |
| `Master/Filesystem.md` | Directory structure, file/folder naming, image conventions |
| `Master/CourseStructure.md` | Page types (Overview, Lesson, Summary) with full templates |
| `Master/Formatting.md` | Images, two-column layouts, code blocks, admonitions, tables |
| `Master/Language.md` | Voice, tone, humour, word choices, platform names |
| `Master/HOWTO.md` | End-to-end workflows: create, publish, remove, review, validate |
| `Master/Localization.md` | Translation rules and glossary (dormant until localization starts) |

---

## Quick Reference (always in context)

### Language essentials
- **Second person, direct:** "you'll configure", "your agent", "open the panel"
- **Short sentences.** One idea per sentence. Paragraphs: 2–4 sentences max.
- **Avoid:** "leverage", "utilize", "robust", "seamlessly", "In this section we will", "Please note that", "It is important to", "feel free to"
- **Platform names:** Bold on first appearance per page. Exact names: **Maestro**, **IXP**, **Action Center**, **Studio Web**, **Data Fabric**, **Integration Service**, **Orchestrator**

### Formatting essentials
- **Code blocks:** Every copyable text in a fenced code block with a language identifier. Never bare ` ``` `.
- **Screenshots:** `{ .screenshot }` for all UI screenshots. Wide images (`-W`) use `width="900"`.
- **Two-column:** `[[[...|N|...]]]` shorthand (processed by `hooks/split_cols.py`).
- **Admonitions:** Only `tip`, `info`, `note`, `warning`.
- **No bottom nav links.** MkDocs sidebar handles navigation.

### File naming
- Section folder: lowercase, hyphenated (`prepare`, `build`)
- Overview: always `index.md`
- Lessons: `N-verb-noun.md` (`1-extract-the-documents.md`)
- Images: per-lesson folders (`<lesson-slug>.images/`)

---

## Behavioural Rules

- New pages start as **drafts** — not in `nav:` in `mkdocs.yml` (use
  `mkdocs.local.yml` for preview). `/publish-exercise` promotes when ready.
  The `dashboard/` section is currently draft.
- **Never remove sections, paragraphs, or explanatory text** when editing.
  Rephrase — don't delete.
- Stub pages carry an HTML draft marker and a "Planned content" bullet list —
  the approved structure. A content pass replaces the bullets, keeps the scope.
- Run `mkdocs build` before committing. "Page not in navigation" warnings are
  expected for draft sections.

---

## Local Preview

```bash
pip install -r requirements.txt
git submodule update --init
mkdocs serve -f mkdocs.local.yml    # includes draft sections
mkdocs build                        # published nav only — run before committing
```
