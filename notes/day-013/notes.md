# Notes — Day 013

## Important Concepts

### 1. DVC Pull

Command:

```bash
dvc pull
```

downloads datasets and artifacts from configured remote storage.

---

## 2. DVC Pointer Files

Example:

```text
transactions.csv.dvc
```

The `.dvc` file stores metadata about the dataset but not the dataset itself.

---

## 3. Local DVC Cache

DVC stores downloaded datasets inside a local cache for:

- deduplication
- faster restores
- efficient storage management

---

## 4. S3 Authentication

S3-compatible storage requires:

- access key
- secret key

Example:

```ini
access_key_id = weedadmin
secret_access_key = weedadmin123
```

---

## 5. SeaweedFS Integration

SeaweedFS provides:

- S3-compatible APIs
- distributed object storage
- scalable remote dataset storage

---

## 6. DVC Status Check

Command:

```bash
dvc status -c
```

checks synchronization between:

- workspace
- local cache
- remote storage

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Access key configured | ✅ |
| Secret key configured | ✅ |
| Remote authentication working | ✅ |
| Dataset restored successfully | ✅ |
| DVC cache synchronized | ✅ |
| `dvc pull` completed successfully | ✅ |