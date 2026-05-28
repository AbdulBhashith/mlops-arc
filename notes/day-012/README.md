# Day-012: Configure a DVC Remote Storage

## Overview

This lab focused on configuring a DVC remote storage backend using SeaweedFS as an S3-compatible object store for the `fraud-detection` ML project.

The task involved:

- Reviewing the existing DVC remote configuration
- Correcting the remote bucket configuration
- Updating the SeaweedFS S3 endpoint
- Setting the default DVC remote
- Pushing tracked datasets to remote storage

---

## Technologies Used

- DVC
- SeaweedFS
- S3-Compatible Storage
- Git
- MLOps

---

## Skills Practiced

- DVC remote configuration
- Object storage integration
- S3-compatible storage management
- Dataset synchronization
- Remote artifact storage

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-configure-dvc-remote-storage.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully configured SeaweedFS as the default DVC remote storage and pushed tracked datasets to the remote bucket:

```text
s3://dvc-storage
```

The DVC-tracked dataset is now stored remotely under the SeaweedFS object storage backend.