# Day-018: Version Datasets and Models Across Git Branches

## Overview

This lab focused on managing different dataset and model versions across Git branches using DVC.

The task involved:

- Tagging the current project state as `v1.0`
- Creating a new branch for improved data
- Replacing the tracked dataset
- Re-training the ML pipeline
- Committing the new dataset version
- Restoring the original dataset on the main branch using DVC

---

## Technologies Used

- Git
- DVC
- Python
- Machine Learning
- MLOps

---

## Skills Practiced

- Git branching strategies
- Dataset versioning with DVC
- Model reproducibility
- Dataset rollback
- Branch-specific ML workflows

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-version-datasets-across-branches.md` | Detailed lab walkthrough |
| `commands.md` | Commands used during the lab |
| `notes.md` | Key concepts and troubleshooting notes |

---

## Outcome

Successfully created two dataset versions:

### Main Branch

```text
Version: v1.0
Dataset: transactions.csv (original)
```

### v2-improved Branch

```text
Version: v2-improved
Dataset: transactions_v2.csv (improved)
```

DVC correctly restored the original dataset when switching back to the main branch.