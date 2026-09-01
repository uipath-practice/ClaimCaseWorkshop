# ClaimCase Workshop

Participant handbook for the ClaimCase workshop: build an enterprise
property-claims solution end-to-end with coding agents — design, plan, six
build blocks, verification against planted problems, and handover.

**Status: structure only.** Pages are approved outlines awaiting the content
pass. GitHub Pages is not enabled yet.

## How this repo works

- MkDocs Material site; content in `docs/`, one folder per workshop stage
  (Prepare → Plan → Build → Verify), navigation in `mkdocs.yml`.
- The exercise seed lives in its own repo,
  [PropertyClaimsSeeds](https://github.com/uipath-practice/PropertyClaimsSeeds),
  mounted here as the `seeds/` submodule. Lesson pages transclude the seed's
  prompts at build time (`pymdownx.snippets`), so the course always shows the
  exact prompt participants run. The pinned submodule commit is the frozen
  seed version for a cohort.
- Training-environment values (URL, tenant) are macros from `main.py`,
  switched with `COURSE_ENV` (staging | prod).
- Authoring rules and templates: `Master/` (see `CLAUDE.md` for the always-on
  subset). Draft sections stay out of `mkdocs.yml` nav; preview them with
  `mkdocs.local.yml`.
- Localization is wired (`mkdocs-static-i18n`) but dormant — English only for
  now.

## Local preview

```bash
pip install -r requirements.txt
git submodule update --init
mkdocs serve -f mkdocs.local.yml   # includes draft sections
mkdocs build                       # what CI deploys
```

Deploy: GitHub Actions (`.github/workflows/deploy.yml`) publishes to the
`gh-pages` branch on every push to `main`.
