# Lab 01 — Create a Makefile for ML Workflow Automation

## Objective

Fix and standardize the Makefile for the `fraud-detection` ML project so common workflows can be automated successfully.

---

## Task Summary

The provided Makefile had multiple issues:

- Missing `.PHONY` declarations
- Incorrect target sequence
- Missing `data` target in `all`
- Improper cleanup commands
- Invalid indentation using spaces instead of tabs

The goal was to correct the Makefile so `make all` runs successfully.

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Step 1 — Navigate to Project Directory

```bash
cd /root/code/fraud-detection
```

---

## Step 2 — Run Existing Makefile

```bash
make all
```

### Purpose

Helps identify existing Makefile issues and workflow failures.

---

## Step 3 — Inspect Existing Problems

### Issues Found

| Problem | Description |
|---------|-------------|
| Missing `.PHONY` | Targets could conflict with filenames |
| Wrong indentation | `make` requires tab indentation |
| Missing `data` target in `all` | Workflow incomplete |
| Incomplete cleanup | Did not remove all cache files |
| Improper virtual environment path usage | Environment setup inconsistency |

---

## Step 4 — Correct the Makefile

### Updated Makefile

```Makefile
.PHONY: setup data train test clean all

setup:
	python3 -m venv mlops-venv
	./mlops-venv/bin/pip install -r requirements.txt

data:
	python src/data/process_data.py

train:
	python src/models/train.py

test:
	pytest tests/

clean:
	find . -type d -name "__pycache__" -exec rm -rf {} +
	rm -rf .pytest_cache
	rm -rf models/*

all: setup data train test
```

---

## Step 5 — Run Automated Workflow

```bash
make all
```

### Workflow Execution Order

1. setup
2. data
3. train
4. test

---

## Verification

Verify workflow execution completed successfully.

Check virtual environment:

```bash
ls mlops-venv
```

Check generated models:

```bash
ls models/
```

---

## Errors & Fixes

### Error 1 — Missing Tab Indentation

#### Error

```text
missing separator
```

#### Cause

Recipes used spaces instead of tabs.

#### Fix

Replaced spaces with real tab characters.

---

### Error 2 — Missing data Target in all

#### Problem

The workflow skipped the data processing stage.

#### Fix

Updated:

```Makefile
all: setup data train test
```

---

### Error 3 — Incomplete Cleanup

#### Problem

Only root `__pycache__` directories were removed.

#### Fix

Added recursive cleanup:

```bash
find . -type d -name "__pycache__" -exec rm -rf {} +
```

---

## Key Learnings

- Makefiles automate repetitive ML workflows
- `.PHONY` prevents conflicts between targets and filenames
- Makefile recipes must use tabs, not spaces
- Workflow sequencing is important in ML pipelines
- Cleanup targets help maintain clean development environments

---

## Real-World Relevance

Makefiles are widely used in:

- MLOps projects
- CI/CD pipelines
- ML training automation
- DevOps workflows
- Reproducible engineering environments