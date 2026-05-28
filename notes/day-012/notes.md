# Notes — Day 012

## Important Concepts

### 1. DVC Remote Storage

DVC remotes are external storage backends used to store:

- datasets
- model artifacts
- cached ML files

---

## 2. SeaweedFS

SeaweedFS is a distributed object storage system that supports:

- S3-compatible APIs
- scalable storage
- distributed file management

---

## 3. S3-Compatible Storage

DVC can integrate with any storage system supporting the S3 API.

Example:

```text
http://localhost:8333
```

---

## 4. DVC Remote Configuration

Remote settings are stored inside:

```text
.dvc/config
```

Example:

```ini
[core]
    remote = s3
```

---

## 5. DVC Push

Command:

```bash
dvc push
```

uploads tracked datasets to remote storage.

---

## 6. Object Storage Layout

DVC stores objects using hash-based paths:

```text
files/md5/
```

This improves:

- deduplication
- caching
- efficient storage management

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Bucket name corrected | ✅ |
| Endpoint URL updated | ✅ |
| Default remote configured | ✅ |
| DVC push successful | ✅ |
| Remote objects visible | ✅ |
```