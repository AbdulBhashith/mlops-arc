# Lab 01 — Set Up Code Quality Tools for ML Code

## Objective

Fix and configure the project so `ruff` and `black` pass successfully for all source files.

---

## Task Summary

The project contained incorrect linting and formatting configurations that caused failures during validation.

The goal was to:

- Correct the `pyproject.toml`
- Update Ruff configuration schema
- Standardize line length settings
- Fix linting and formatting issues in source files
- Ensure all checks pass successfully

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Step 1 — Inspect Existing Configuration

Open the existing configuration:

```bash
cat pyproject.toml
```

### Existing Configuration

```toml
[project]
name = "fraud-detection"
version = "0.1.0"

[tool.ruff]
line-length = 88
select = ["E", "F"]

[tool.black]
line-length = 100
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| Ruff line length mismatch | Required 120 |
| Black line length mismatch | Required 120 |
| Old Ruff schema | `select` must be under `[tool.ruff.lint]` |
| Missing lint rules | Required E, F, W, I |
| Source formatting issues | Black validation failing |
| Lint violations | Ruff validation failing |

---

## Step 2 — Correct pyproject.toml

### Updated Configuration

```toml
[project]
name = "fraud-detection"
version = "0.1.0"

[tool.ruff]
line-length = 120

[tool.ruff.lint]
select = ["E", "F", "W", "I"]

[tool.black]
line-length = 120
```

---

## Step 3 — Fix Source Code Issues

Example issue:

```python
import os
import pandas as pd
```

### Problem

`os` was imported but never used.

### Fix

```python
import pandas as pd
```

---

## Step 4 — Automatically Fix Ruff Issues

Run:

```bash
ruff check src/ --fix
```

### Purpose

Automatically fixes:

- unused imports
- import ordering
- simple lint issues

---

## Step 5 — Format Source Files with Black

Run:

```bash
black src/
```

### Purpose

Formats all Python files according to Black style rules.

---

## Step 6 — Verify All Checks Pass

Run Ruff validation:

```bash
ruff check src/
```

Run Black validation:

```bash
black --check src/
```

---

## Verification

Expected Result:

```text
All checks passed
```

Both commands should exit with status code `0`.

---

## Errors & Fixes

### Error 1 — Ruff Configuration Schema Error

#### Cause

The `select` configuration was placed under `[tool.ruff]`.

#### Fix

Moved configuration to:

```toml
[tool.ruff.lint]
```

---

### Error 2 — Line Length Mismatch

#### Cause

Ruff and Black used different line length values.

#### Fix

Updated both tools to:

```toml
line-length = 120
```

---

### Error 3 — Unused Imports

#### Error

```text
F401 imported but unused
```

#### Fix

Removed unused imports from source files.

---

### Error 4 — Import Ordering Issues

#### Cause

Imports were not sorted properly.

#### Fix

Used:

```bash
ruff check src/ --fix
```

---

## Key Learnings

- Ruff provides fast Python linting and import sorting
- Black ensures consistent code formatting
- Shared line-length settings prevent formatting conflicts
- Proper linting improves code quality and maintainability
- Automated formatting reduces manual cleanup effort

---

## Real-World Relevance

Code quality tooling is essential in:

- MLOps projects
- CI/CD pipelines
- Team collaboration workflows
- Production ML systems
- Enterprise software development