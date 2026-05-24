# Lab 01 — Configure Pre-Commit Hooks for ML Repository

## Objective

Fix and standardize the pre-commit configuration so all required hooks execute successfully.

---

## Task Summary

The provided `.pre-commit-config.yaml` contained several issues:

- Incorrect hook names
- Missing version pins
- Outdated repository URLs
- Invalid Ruff hook configuration

The goal was to correct the configuration and ensure all hooks run successfully.

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Step 1 — Inspect Existing Configuration

View the existing configuration:

```bash
cat .pre-commit-config.yaml
```

### Existing Configuration

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v2.3.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check_yaml

  - repo: https://github.com/charliermarsh/ruff-pre-commit
    rev: v0.1.0
    hooks:
      - id: ruff-lint

  - repo: https://github.com/psf/black-pre-commit-mirror
    hooks:
      - id: black
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| `check_yaml` incorrect | Should be `check-yaml` |
| Ruff repository outdated | Old repository URL |
| Invalid Ruff hook ID | Should be `ruff` |
| Missing `rev` field | Required for every repository |
| Outdated versions | Needed current releases |

---

## Step 2 — Correct .pre-commit-config.yaml

### Updated Configuration

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml

  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.11.13
    hooks:
      - id: ruff

  - repo: https://github.com/psf/black-pre-commit-mirror
    rev: 25.1.0
    hooks:
      - id: black
```

---

## Step 3 — Install Git Hooks

Run:

```bash
pre-commit install
```

### Purpose

Registers pre-commit hooks inside the Git repository.

---

## Step 4 — Run Hooks Against All Files

Run:

```bash
pre-commit run --all-files
```

### Purpose

Executes all configured hooks against tracked files.

---

## Verification

Expected Result:

```text
Passed
```

All hooks should complete successfully.

---

## Errors & Fixes

### Error 1 — Invalid Hook Name

#### Problem

Used:

```yaml
check_yaml
```

#### Fix

Updated to:

```yaml
check-yaml
```

---

### Error 2 — Outdated Ruff Repository

#### Problem

The Ruff repository URL was deprecated.

#### Fix

Updated to:

```yaml
https://github.com/astral-sh/ruff-pre-commit
```

---

### Error 3 — Missing rev Field

#### Problem

The Black repository configuration lacked a version pin.

#### Fix

Added:

```yaml
rev: 25.1.0
```

---

### Error 4 — Invalid Ruff Hook ID

#### Problem

Used:

```yaml
id: ruff-lint
```

#### Fix

Updated to:

```yaml
id: ruff
```

---

## Key Learnings

- Pre-commit automates code quality checks before commits
- Every repository entry should include a pinned `rev`
- Ruff and Black integrate well with Git workflows
- Automated hooks reduce manual code review effort
- YAML formatting must be precise for hook loading

---

## Real-World Relevance

Pre-commit hooks are widely used in:

- MLOps repositories
- CI/CD pipelines
- Team development workflows
- Enterprise Git standards
- Automated code quality systems