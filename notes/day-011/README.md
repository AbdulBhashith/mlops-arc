# Day-011: Track a Dataset with DVC

## Overview

This lab focused on migrating dataset tracking from Git to DVC inside the `fraud-detection` repository.

The task involved:

- Removing dataset tracking from Git
- Preserving the dataset on disk
- Adding the dataset to DVC
- Generating a `.dvc` pointer file
- Updating `.gitignore`
- Committing the DVC tracking changes

---

## Technologies Used

- Git
- DVC
- Python
- MLOps
- Data Versioning

---

## Skills Practiced

- DVC dataset tracking
- Git untracking workflows
- Dataset version management
- ML repository organization
- Data reproducibility practices

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-track-dataset-with-dvc.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully migrated the dataset tracking workflow from Git to DVC.

The dataset:

```text
data/raw/transactions.csv
```

is now managed through DVC using a lightweight `.dvc` pointer file while the actual dataset remains outside Git tracking.