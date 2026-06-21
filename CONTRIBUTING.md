# Contributing to UgCore Framework

Thank you for taking the time to contribute. This document covers everything you need to know before opening an issue or submitting a pull request.

This guide applies to all repositories under the **UgCore Framework** organization.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Ways to Contribute](#ways-to-contribute)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Development Setup](#development-setup)
- [Branch & Commit Conventions](#branch--commit-conventions)
- [Submitting a Pull Request](#submitting-a-pull-request)
- [Review Process](#review-process)
- [Release Cycle](#release-cycle)

---

## Code of Conduct

We expect all contributors to treat others with respect. Harassment, discrimination, or hostile behaviour will result in removal from the project. When in doubt, be kind.

---

## Ways to Contribute

You do not need to write code to contribute. Other valuable contributions include:

- Reporting bugs with clear reproduction steps
- Improving documentation or correcting typos
- Testing pre-release builds on `dev` and reporting regressions
- Answering community questions on Discord or GitHub Discussions
- Reviewing open pull requests and leaving constructive feedback

---

## Reporting Bugs

Before opening a bug report:

1. Check if the issue already exists in [open issues](../../issues)
2. Make sure you are running the **latest release**
3. Confirm that the issue is related to UgCore or an official UgCore resource. We are not responsible for bugs caused by customized or modified resources.

When you open a bug report, use the **Bug Report** issue template and fill in every field. Incomplete reports may be closed without investigation.

> **Security vulnerabilities must not be reported as public issues.** See [SECURITY.md](SECURITY.md) for the correct process.

---

## Suggesting Features

Open a **Feature Request** issue and describe:

- The problem you are trying to solve
- Your proposed solution
- Any alternatives you considered

Features that align with UgCore's philosophy — lightweight, modular, developer-friendly — are more likely to be accepted. Large additions that could live as a separate resource will generally be declined in favour of keeping the core lean.

---

## Development Setup

### Prerequisites

- A working FiveM server (latest recommended artifact)
- MySQL 8.x or MariaDB 10.6+
- [oxmysql](https://github.com/overextended/oxmysql)
- [Git](https://git-scm.com)

### Local Setup

```bash
# 1. Fork the repository on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/ug-core.git
cd ug-core

# 2. Add the upstream remote
git remote add upstream https://github.com/ugcore-framework/ug-core.git

# 3. Copy the resource into your FiveM server's resources folder
# and add `ensure ug-core` to server.cfg
```

### Staying Up to Date

```bash
git fetch upstream
git rebase upstream/dev
```

Always branch off `dev`, not `main`.

---

## Branch & Commit Conventions

### Branch Names

```
feature/short-description     ← new functionality
fix/short-description         ← bug fixes
hotfix/short-description      ← urgent fix on main
docs/short-description        ← documentation only
refactor/short-description    ← code changes with no behaviour change
chore/short-description       ← tooling, CI, dependencies
```

### Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

feat(player): add shared object caching
fix(database): handle null identifier on character load
docs(exports): document GetPlayer return shape
chore(ci): update luacheck version
```

**Allowed types:** `feat`, `fix`, `hotfix`, `chore`, `docs`, `refactor`, `perf`, `test`, `ci`

**Allowed scopes:** `core`, `player`, `jobs`, `gangs`, `permissions`, `database`, `exports`, `config`, `ci`, `deps`

Rules:
- Subject starts with a lowercase letter
- Subject is in the imperative mood ("add", not "added" or "adds")
- No period at the end of the subject line
- Keep the subject under 72 characters

---

## Submitting a Pull Request

1. **Branch off `dev`** — never off `main`
2. Keep PRs focused — one feature or fix per PR
3. Update relevant documentation if your change affects public exports or configuration
4. If your change requires a SQL migration, add it to `sql/migrations/vX.Y.Z.sql`
5. Make sure your PR title follows the Conventional Commits format (our CI will check this)
6. Fill in the pull request template completely

### PR Title Examples

```
✅ feat(player): add character slot selection
✅ fix(jobs): correct grade level lookup on duty toggle
✅ docs(exports): add SetJob usage example

❌ Fixed bug
❌ Updates
❌ WIP
```

### Draft PRs

If your work is not ready for review, open it as a **Draft PR**. This signals to maintainers that it is a work in progress and prevents premature review.

---

## Review Process

All pull requests must pass the following before merging:

- ✅ CI checks pass (lint, fxmanifest validation)
- ✅ PR title follows Conventional Commits
- ✅ At least **1 approval** from a Maintainer (merges into `dev`)
- ✅ **Lead Developer approval** required for merges into `main`

Reviewers may request changes. Please address feedback promptly. PRs with no activity for 14 days may be closed.

### Who Merges What

| Target Branch | Who Can Merge |
|---|---|
| `dev` | Maintainers or Lead Developer |
| `main` | Lead Developer only |

---

## Release Cycle

We use [Semantic Versioning](https://semver.org/) — `vMAJOR.MINOR.PATCH`.

| Change | Version Bump |
|---|---|
| Breaking changes (config, exports, DB schema) | MAJOR |
| New backwards-compatible features | MINOR |
| Bug fixes and small improvements | PATCH |

Releases are cut from `main` by the Lead Developer. If your contribution is merged into `dev`, it will be included in the next release when `dev` is merged into `main` and tagged.

If your change introduces a **breaking change**, call it out explicitly in your PR description. It will be documented in the release changelog under `⚠️ Breaking Changes`.

---

## Questions?

If you are unsure about anything before opening a PR, ask in the **#dev** channel on our [Discord server](https://discord.gg/pCJUcyVw5X). We would rather answer a question upfront than have you spend time on something that will not be accepted.
