# Lab 01 — Fix DVC Pull Authentication and Restore Dataset

## Objective

Correct the DVC remote authentication configuration and restore the missing dataset from SeaweedFS storage.

---

## Task Summary

The repository already contained:

- DVC initialization
- A `.dvc` pointer file
- Configured remote storage

However:

- the dataset was missing locally
- the local DVC cache was empty
- `dvc pull` failed due to authentication issues

The goal was to:

- fix DVC remote credentials
- authenticate successfully
- restore the dataset from remote storage

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## SeaweedFS Details

| Component | Value |
|-----------|------|
| S3 Endpoint | `http://localhost:8333` |
| Bucket Name | `dvc-storage` |
| Access Key | `weedadmin` |
| Secret Key | `weedadmin123` |

---

## Existing Incorrect Configuration

```ini
[core]
    remote = s3

['remote "s3"']
    url = s3://dvc-storage
    endpointurl = http://localhost:8333
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| Missing access key | Authentication failed |
| Missing secret key | Remote access denied |

---

## Step 1 — Navigate to Repository

```bash
cd /root/code/fraud-detection
```

---

## Step 2 — Add Access Key

Run:

```bash
dvc remote modify s3 access_key_id weedadmin
```

### Purpose

Adds the SeaweedFS S3 access key.

---

## Step 3 — Add Secret Key

Run:

```bash
dvc remote modify s3 secret_access_key weedadmin123
```

### Purpose

Adds the SeaweedFS S3 secret key.

---

## Step 4 — Verify Updated Configuration

Expected `.dvc/config`:

```ini
[core]
    remote = s3

['remote "s3"']
    url = s3://dvc-storage
    endpointurl = http://localhost:8333
    access_key_id = weedadmin
    secret_access_key = weedadmin123
```

---

## Step 5 — Pull Dataset from Remote Storage

Run:

```bash
dvc pull
```

### Purpose

Downloads the tracked dataset from the configured DVC remote.

---

## Step 6 — Verify Dataset Restoration

Check dataset:

```bash
ls data/raw/
```

Expected Result:

```text
transactions.csv
transactions.csv.dvc
```

---

## Step 7 — Verify DVC Cache Status

Run:

```bash
dvc status -c
```

### Purpose

Confirms that the local workspace and cache match the remote-tracked version.

Expected Result:

```text
up to date
```

---

## Errors & Fixes

### Error 1 — Authentication Failure

#### Cause

The DVC remote lacked authentication credentials.

#### Fix

Added:

```bash
dvc remote modify s3 access_key_id weedadmin
dvc remote modify s3 secret_access_key weedadmin123
```

---

### Error 2 — Dataset Missing Locally

#### Cause

The repository only contained the `.dvc` pointer file.

#### Fix

Run:

```bash
dvc pull
```

to restore the actual dataset from remote storage.

---

## Key Learnings

- DVC requires authentication for protected remote storage
- `.dvc` files only store metadata pointers
- `dvc pull` restores tracked datasets from remotes
- DVC caches datasets locally after download
- S3-compatible remotes require valid credentials

---

## Real-World Relevance

DVC pull workflows are widely used in:

- collaborative ML projects
- cloud-based ML pipelines
- remote dataset synchronization
- reproducible experiment setups
- enterprise MLOps platforms