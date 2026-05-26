# Lab 01 — Install and Initialize DVC in an ML Project

## Objective

Initialize DVC inside an existing Git repository and track the generated configuration files using Git.

---

## Task Summary

The `fraud-detection` repository already existed as a Git repository, but DVC was not configured.

The goal was to:

- Initialize DVC
- Create the `.dvc/` control directory
- Generate `.dvcignore`
- Stage generated files
- Commit the initialization changes

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Step 1 — Navigate to Repository

```bash
cd /root/code/fraud-detection/
```

### Purpose

Moves into the existing ML project repository.

---

## Step 2 — Initialize DVC

Run:

```bash
dvc init
```

### Purpose

Initializes DVC inside the Git repository.

This creates:

```text
.dvc/
.dvcignore
```

---

## Step 3 — Verify Generated Files

Check repository contents:

```bash
ls -a
```

Expected Result:

```text
.dvc
.dvcignore
```

---

## Step 4 — Stage DVC Files

Add generated files to Git:

```bash
git add .dvc .dvcignore
```

### Purpose

Stages DVC configuration files for version control.

---

## Step 5 — Commit Initialization

Create a Git commit:

```bash
git commit -m "Initialize DVC"
```

### Purpose

Records DVC initialization in repository history.

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

Verify commit history:

```bash
git log --oneline
```

Expected Result:

```text
Initialize DVC
```

---

## Errors & Fixes

### Error 1 — Not Inside a Git Repository

#### Error

```text
ERROR: failed to initiate DVC - not a git repository
```

#### Cause

DVC requires a Git repository.

#### Fix

Ensure commands are run inside:

```bash
/root/code/fraud-detection/
```

---

### Error 2 — Untracked DVC Files

#### Problem

DVC files were created but not committed.

#### Fix

Stage and commit:

```bash
git add .dvc .dvcignore
git commit -m "Initialize DVC"
```

---

## Key Learnings

- DVC integrates tightly with Git repositories
- DVC separates large data and model tracking from source code
- `.dvc/` stores DVC project metadata
- `.dvcignore` excludes files from DVC tracking
- DVC improves reproducibility in ML workflows

---

## Real-World Relevance

DVC is widely used in:

- MLOps pipelines
- ML experiment tracking
- Large dataset management
- Model versioning systems
- Collaborative machine learning projects