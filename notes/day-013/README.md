# Day-013: Fix DVC Pull Authentication and Restore Dataset

## Overview

This lab focused on troubleshooting and fixing DVC remote authentication issues in a cloned ML repository.

The task involved:

- Diagnosing why `dvc pull` failed
- Reviewing the DVC remote configuration
- Adding missing SeaweedFS credentials
- Restoring the dataset from remote storage
- Verifying DVC cache synchronization

---

## Technologies Used

- DVC
- SeaweedFS
- Git
- S3-Compatible Storage
- MLOps

---

## Skills Practiced

- DVC troubleshooting
- Remote authentication setup
- Dataset restoration
- DVC cache synchronization
- ML data recovery workflows

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-fix-dvc-pull-authentication.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully fixed the DVC remote authentication issue and restored the dataset:

```text
data/raw/transactions.csv
```

The repository can now pull datasets correctly from the SeaweedFS remote storage backend.