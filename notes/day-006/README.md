# Day-006: Set Up Code Quality Tools for ML Code

## Overview

This lab focused on configuring and fixing code quality tooling for the `fraud-detection` ML project using `ruff` and `black`.

The task involved:

- Correcting the `pyproject.toml` configuration
- Updating Ruff lint configuration syntax
- Standardizing line length settings
- Fixing source code linting issues
- Ensuring formatting compliance with Black

---

## Technologies Used

- Python
- Ruff
- Black
- pyproject.toml
- Code Quality Tooling

---

## Skills Practiced

- Python linting
- Code formatting
- Static code analysis
- Tool configuration
- Clean code practices

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-setup-code-quality-tools.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully configured the project so both commands completed without errors:

```bash
ruff check src/
black --check src/
```

The project now follows standardized code quality rules with:

- Line length: 120
- Ruff lint rules: E, F, W, I
- Black formatting consistency