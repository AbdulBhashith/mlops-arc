# Commands Used — Day 013

## Navigate to Repository

```bash
cd /root/code/fraud-detection
```

---

## Configure SeaweedFS Access Key

```bash
dvc remote modify s3 access_key_id weedadmin
```

---

## Configure SeaweedFS Secret Key

```bash
dvc remote modify s3 secret_access_key weedadmin123
```

---

## Pull Dataset from Remote Storage

```bash
dvc pull
```

---

## Verify Dataset Files

```bash
ls data/raw/
```

---

## Verify DVC Cache Status

```bash
dvc status -c
```