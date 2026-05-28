# Lab 01 — Configure a DVC Remote Storage

## Objective

Fix the DVC remote configuration and push tracked datasets to the SeaweedFS S3-compatible storage backend.

---

## Task Summary

The project already contained:

- DVC initialization
- A tracked dataset
- A preconfigured DVC remote named `s3`

However, the remote configuration was incorrect, causing `dvc push` to fail.

The goal was to:

- Correct the bucket configuration
- Fix the endpoint URL
- Set the remote as default
- Push tracked data successfully

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
['remote "s3"']
    url = s3://dvc-wrong-bucket
    endpointurl = http://localhost:9999
    access_key_id = weedadmin
    secret_access_key = weedadmin123
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| Incorrect bucket name | Wrong S3 bucket configured |
| Invalid endpoint URL | Wrong SeaweedFS port |
| Missing default remote | Remote not configured as default |

---

## Step 1 — Navigate to Repository

```bash
cd /root/code/fraud-detection/
```

---

## Step 2 — Correct Remote Bucket

Run:

```bash
dvc remote modify s3 url s3://dvc-storage
```

### Purpose

Updates the remote to use the correct SeaweedFS bucket.

---

## Step 3 — Correct SeaweedFS Endpoint

Run:

```bash
dvc remote modify s3 endpointurl http://localhost:8333
```

### Purpose

Configures the correct SeaweedFS S3-compatible endpoint.

---

## Step 4 — Set Default Remote

Run:

```bash
dvc remote default s3
```

### Purpose

Marks `s3` as the default DVC remote.

---

## Step 5 — Verify Updated Configuration

Expected `.dvc/config`:

```ini
[core]
    remote = s3

['remote "s3"']
    url = s3://dvc-storage
    access_key_id = weedadmin
    secret_access_key = weedadmin123
    endpointurl = http://localhost:8333
```

---

## Step 6 — Push Dataset to Remote Storage

Run:

```bash
dvc push
```

### Purpose

Uploads DVC-tracked files into the SeaweedFS object store.

---

## Verification

Verify remote storage objects:

```bash
aws --endpoint-url http://localhost:8333 \
    s3 ls s3://dvc-storage/files/md5/ \
    --recursive \
    --profile default
```

Expected Result:

```text
files/md5/...
```

Objects should exist inside the bucket.

---

## Errors & Fixes

### Error 1 — Invalid Bucket Name

#### Cause

Configured bucket:

```text
dvc-wrong-bucket
```

#### Fix

Updated to:

```text
dvc-storage
```

---

### Error 2 — Incorrect Endpoint URL

#### Cause

Wrong SeaweedFS port:

```text
http://localhost:9999
```

#### Fix

Updated to:

```text
http://localhost:8333
```

---

### Error 3 — No Default Remote

#### Cause

DVC remote existed but was not set as default.

#### Fix

Run:

```bash
dvc remote default s3
```

---

## Key Learnings

- DVC supports S3-compatible object storage systems
- SeaweedFS can function as a DVC remote backend
- Remote configuration is stored inside `.dvc/config`
- DVC separates dataset storage from Git repositories
- Object storage improves scalable ML workflows

---

## Real-World Relevance

DVC remote storage is widely used in:

- Enterprise MLOps platforms
- Cloud ML pipelines
- Distributed dataset management
- Scalable artifact storage
- Collaborative machine learning systems