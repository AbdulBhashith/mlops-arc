# Day-008: Configure Pre-Commit Hooks for ML Repository

## Overview

This lab focused on configuring and fixing pre-commit hooks for the `fraud-detection` ML repository.

The task involved:

- Reviewing the existing `.pre-commit-config.yaml`
- Fixing invalid hook names
- Updating outdated repositories
- Adding missing version pins
- Registering Git hooks
- Running automated quality checks on all tracked files

---

## Technologies Used

- Git
- pre-commit
- Ruff
- Black
- YAML

---

## Skills Practiced

- Git hook automation
- Pre-commit configuration
- Code quality enforcement
- YAML troubleshooting
- Automated linting workflows

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-configure-pre-commit-hooks.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully configured the repository with working pre-commit hooks for:

- trailing-whitespace
- end-of-file-fixer
- check-yaml
- ruff
- black

All hooks executed successfully using:

```bash
pre-commit run --all-files
```