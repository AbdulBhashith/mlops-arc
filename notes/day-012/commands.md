# Commands Used — Day 012

## Navigate to Repository

```bash
cd /root/code/fraud-detection/
```

---

## Update Remote Bucket

```bash
dvc remote modify s3 url s3://dvc-storage
```

---

## Update SeaweedFS Endpoint

```bash
dvc remote modify s3 endpointurl http://localhost:8333
```

---

## Set Default DVC Remote

```bash
dvc remote default s3
```

---

## Push Tracked Data

```bash
dvc push
```

---

## Verify Remote Storage Objects

```bash
aws --endpoint-url http://localhost:8333 \
    s3 ls s3://dvc-storage/files/md5/ \
    --recursive \
    --profile default
```