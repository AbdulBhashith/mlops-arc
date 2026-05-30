# Lab 01 — Create a DVC Pipeline for Data Processing

## Objective

Fix the DVC pipeline configuration so data processing and dataset splitting execute successfully in a reproducible workflow.

---

## Task Summary

The existing `dvc.yaml` contained incorrect commands, outputs, and dependencies that prevented the pipeline from executing completely.

The goal was to:

- Correct stage definitions
- Configure proper dependencies
- Define expected outputs
- Execute the pipeline successfully
- Verify pipeline status

---

## Project Directory

```bash
/ root/code/fraud-detection/
```

---

## Existing Pipeline Configuration

```yaml
stages:
  process_data:
    cmd: python src/data/process.py
    deps:
      - data/raw/transactions.csv
      - src/data/process_data.py
    outs:
      - data/processed/clean.csv

  split_data:
    cmd: python src/data/split_data.py
    deps:
      - src/data/split_data.py
    outs:
      - data/processed/train.csv
      - data/processed/test.csv
```

---

## Problems Identified

| Problem | Description |
|----------|-------------|
| Wrong script path | `process.py` does not match required script |
| Wrong output file | Output filename incorrect |
| Missing dependency | `split_data` missing processed dataset dependency |

---

## Step 1 — Correct dvc.yaml

Replace the existing file with:

```yaml
stages:
  process_data:
    cmd: python src/data/process_data.py
    deps:
      - data/raw/transactions.csv
      - src/data/process_data.py
    outs:
      - data/processed/clean_transactions.csv

  split_data:
    cmd: python src/data/split_data.py
    deps:
      - data/processed/clean_transactions.csv
      - src/data/split_data.py
    outs:
      - data/processed/train.csv
      - data/processed/test.csv
```

---

## Pipeline Flow

```text
transactions.csv
        │
        ▼
process_data
        │
        ▼
clean_transactions.csv
        │
        ▼
split_data
       ├── train.csv
       └── test.csv
```

---

## Step 2 — Reproduce Pipeline

Run:

```bash
dvc repro
```

### Purpose

Executes all pipeline stages in dependency order.

Expected execution:

```text
process_data
split_data
```

---

## Step 3 — Verify Pipeline Status

Run:

```bash
dvc status
```

### Purpose

Checks whether any pipeline stages are outdated.

Expected Result:

```text
Data and pipelines are up to date.
```

---

## Verification

Verify generated outputs:

```bash
ls data/processed/
```

Expected Result:

```text
clean_transactions.csv
train.csv
test.csv
```

---

## Errors & Fixes

### Error 1 — Wrong Processing Script

#### Problem

```yaml
cmd: python src/data/process.py
```

#### Fix

```yaml
cmd: python src/data/process_data.py
```

---

### Error 2 — Incorrect Output File

#### Problem

```yaml
data/processed/clean.csv
```

#### Fix

```yaml
data/processed/clean_transactions.csv
```

---

### Error 3 — Missing Dependency

#### Problem

The `split_data` stage did not depend on the processed dataset.

#### Fix

Added:

```yaml
deps:
  - data/processed/clean_transactions.csv
  - src/data/split_data.py
```

---

## Key Learnings

- DVC pipelines track dependencies and outputs automatically
- Every stage should explicitly define inputs and outputs
- Pipeline stages execute according to dependency order
- `dvc repro` recreates outputs when dependencies change
- Reproducible pipelines improve ML workflow reliability

---

## Real-World Relevance

DVC pipelines are commonly used in:

- Data engineering workflows
- Feature engineering pipelines
- Model training automation
- MLOps platforms
- Production ML systems