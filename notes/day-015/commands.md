# Commands Used — Day 015

## Navigate to Project Directory

```bash
cd /root/code/fraud-detection
```

---

## View Parameters

```bash
cat params.yaml
```

---

## Run Complete Pipeline

```bash
dvc repro
```

---

## Update Parameter

```yaml
n_estimators: 200
```

---

## Reproduce Pipeline After Parameter Change

```bash
dvc repro
```

---

## Verify Pipeline Status

```bash
dvc status
```

---

## Verify Parameter Tracking

```bash
cat dvc.lock
```

---

## Compare Parameter Changes

```bash
git diff params.yaml dvc.lock
```