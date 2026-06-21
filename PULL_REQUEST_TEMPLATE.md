## What does this PR do?

<!-- A clear and concise description of the change. -->

## Related Issue

<!-- Link the issue this PR resolves. Use "Closes #123" to auto-close it on merge. -->

Closes #

## Type of Change

<!-- Check all that apply -->

- [ ] `feat` — new feature
- [ ] `fix` — bug fix
- [ ] `hotfix` — urgent fix on main
- [ ] `refactor` — code change with no behaviour change
- [ ] `perf` — performance improvement
- [ ] `docs` — documentation only
- [ ] `chore` — tooling, CI, dependencies
- [ ] `test` — adding or updating tests

## Breaking Changes

<!-- Does this PR change public exports, config structure, or DB schema in a way that requires server owners to update their setup? -->

- [ ] Yes — describe below
- [ ] No

<!-- If yes, describe what breaks and what server owners need to do: -->

## Testing

<!-- How did you test this change? What should the reviewer test? -->

**Server setup:**
- FiveM artifact:
- UgCore version / branch:

**Steps to test:**
1.
2.
3.

## SQL Migrations

<!-- Does this PR require a database change? -->

- [ ] Yes — migration file added at `sql/migrations/vX.Y.Z.sql`
- [ ] No

## Checklist

- [ ] My PR title follows the Conventional Commits format (`feat(scope): description`)
- [ ] I have branched off `dev`, not `main`
- [ ] I have tested this on a live FiveM server
- [ ] I have updated documentation if this changes public exports or config
- [ ] I have added a migration file if the DB schema changed
