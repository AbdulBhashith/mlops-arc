# Lab 01 — Version Datasets and Models Across Git Branches

## Objective

Manage multiple dataset versions across Git branches while maintaining reproducibility using DVC.

---

## Task Summary

The repository already contained:

```text
data/raw/transactions.csv
```

An improved dataset was also available:

```text
data/raw/transactions_v2.csv
```

The goal was to:

1. Tag the baseline version
2. Create a new development branch
3. Replace the dataset
4. Retrain the pipeline
5. Commit the updated version
6. Restore the original dataset

---

## Project Directory

```bash
/root/code/fraud-detection
```

---

## Initial Dataset State

Tracked dataset:

```text
data/raw/transactions.csv
```

Improved dataset:

```text
data/raw/transactions_v2.csv
```

---

## Step 1 — Switch to Main Branch

```bash
git checkout main
```

Verify:

```bash
git branch --show-current
```

Expected:

```text
main
```

---

## Step 2 — Tag Current Version

Create a release tag:

```bash
git tag v1.0
```

### Purpose

Creates a permanent reference to the baseline dataset and model state.

---

## Step 3 — Create Improved Dataset Branch

```bash
git checkout -b v2-improved
```

Verify:

```bash
git branch --show-current
```

Expected:

```text
v2-improved
```

---

## Step 4 — Replace Dataset

Copy the improved dataset:

```bash
cp data/raw/transactions_v2.csv data/raw/transactions.csv
```

### Purpose

Updates the tracked dataset with newer data.

---

## Step 5 — Update DVC Tracking

Run:

```bash
dvc add data/raw/transactions.csv
```

### Purpose

Generates a new dataset hash and updates the DVC pointer file.

---

## Step 6 — Rebuild the Pipeline

Run:

```bash
dvc repro
```

### Purpose

Recreates:

```text
data/processed/*
models/model.pkl
metrics.json
```

using the updated dataset.

---

## Step 7 — Commit Changes

Stage all updates:

```bash
git add .
```

Commit:

```bash
git commit -m "Use improved dataset and retrain pipeline"
```

---

## Step 8 — Return to Main Branch

```bash
git checkout main
```

---

## Step 9 — Restore Original Dataset

Run:

```bash
dvc checkout
```

### Purpose

Restores files according to the DVC metadata tracked on the main branch.

---

## Step 10 — Verify Current Branch

```bash
git branch --show-current
```

Expected:

```text
main
```

---

## Step 11 — Verify Dataset Matches v1.0

Run:

```bash
git diff v1.0 -- data/raw/transactions.csv.dvc
```

Expected:

```text
(no output)
```

This confirms the dataset matches the tagged version.

---

## Optional Verification

Compare dataset hashes:

### Improved Branch

```bash
git checkout v2-improved
cat data/raw/transactions.csv.dvc
```

### Main Branch

```bash
git checkout main
dvc checkout
cat data/raw/transactions.csv.dvc
```

Expected:

```text
Different md5 values
```

---

## Final State Before Submission

```bash
git checkout main
dvc checkout
```

---

## Verification Checklist

| Check | Result |
|---------|---------|
| v1.0 tag created | ✅ |
| v2-improved branch created | ✅ |
| Dataset replaced | ✅ |
| DVC tracking updated | ✅ |
| Pipeline reproduced | ✅ |
| Changes committed | ✅ |
| Original dataset restored | ✅ |
| Main branch active | ✅ |

---

## Errors & Fixes

### Error 1 — Dataset Not Restored

#### Cause

Forgot to run:

```bash
dvc checkout
```

after switching branches.

#### Fix

Execute:

```bash
dvc checkout
```

to restore tracked files.

---

### Error 2 — No Dataset Hash Change

#### Cause

Skipped:

```bash
dvc add data/raw/transactions.csv
```

#### Fix

Re-add the dataset after replacing the file.

---

### Error 3 — Pipeline Not Updated

#### Cause

New dataset added but pipeline not re-executed.

#### Fix

Run:

```bash
dvc repro
```

to regenerate outputs.

---

## Key Learnings

- Git manages project history
- DVC manages dataset versions
- Dataset versions can differ across branches
- `dvc checkout` restores branch-specific data
- Tags provide stable release points
- Branches support isolated ML experimentation

---

## Real-World Relevance

This workflow is commonly used for:

- Dataset version management
- Model release workflows
- A/B model testing
- ML experimentation
- Production rollback strategies