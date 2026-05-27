# Lab 01 — Track a Dataset with DVC

## Objective

Move dataset tracking from Git to DVC while keeping the dataset file available locally.

---

## Task Summary

The dataset:

```text
data/raw/transactions.csv
```

was incorrectly committed directly to Git.

The goal was to:

- Stop Git tracking the dataset
- Keep the dataset on disk
- Add the dataset to DVC
- Generate DVC tracking files
- Commit the DVC metadata changes

---

## Project Directory

```bash
/root/code/fraud-detection
```

---

## Step 1 — Navigate to Repository

```bash
cd /root/code/fraud-detection
```

---

## Step 2 — Stop Git Tracking the Dataset

Run:

```bash
git rm --cached data/raw/transactions.csv
```

### Purpose

Removes the dataset from Git tracking without deleting the local file.

---

## Step 3 — Track Dataset with DVC

Run:

```bash
dvc add data/raw/transactions.csv
```

### Purpose

Adds the dataset to DVC tracking.

This generates:

```text
data/raw/transactions.csv.dvc
data/raw/.gitignore
```

---

## Step 4 — Stage DVC Tracking Files

Run:

```bash
git add data/raw/transactions.csv.dvc data/raw/.gitignore
```

### Purpose

Stages the DVC metadata files for Git version control.

---

## Step 5 — Commit the Changes

Run:

```bash
git commit -m "Track transactions dataset with DVC"
```

### Purpose

Records the dataset tracking migration in Git history.

---

## Verification

Verify Git status:

```bash
git status
```

Expected Result:

```text
nothing to commit, working tree clean
```

Verify DVC tracking:

```bash
dvc status
```

Verify generated files:

```bash
ls data/raw/
```

Expected Result:

```text
transactions.csv
transactions.csv.dvc
.gitignore
```

---

## Errors & Fixes

### Error 1 — Dataset Deleted Accidentally

#### Cause

Using:

```bash
git rm
```

without `--cached`.

#### Fix

Use:

```bash
git rm --cached data/raw/transactions.csv
```

This keeps the file locally.

---

### Error 2 — Dataset Still Tracked by Git

#### Cause

The `.dvc` file was created but Git still tracked the dataset.

#### Fix

Remove Git tracking first before running:

```bash
dvc add
```

---

### Error 3 — Missing DVC Metadata Files

#### Cause

Forgot to stage generated DVC files.

#### Fix

Stage:

```bash
git add data/raw/transactions.csv.dvc data/raw/.gitignore
```

---

## Key Learnings

- DVC manages large datasets separately from Git
- `.dvc` files act as lightweight dataset pointers
- `.gitignore` prevents large files from entering Git history
- `git rm --cached` removes tracking without deleting files
- DVC improves scalable dataset versioning

---

## Real-World Relevance

DVC dataset tracking is widely used in:

- MLOps pipelines
- Enterprise ML platforms
- Large-scale dataset management
- Experiment reproducibility
- Collaborative machine learning projects