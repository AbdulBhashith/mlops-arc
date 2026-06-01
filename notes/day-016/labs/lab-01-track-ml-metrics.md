# Lab 01 — Track ML Metrics with DVC

## Objective

Configure the DVC training stage to track model evaluation metrics and expose them through DVC commands.

---

## Task Summary

The training script already generated:

```text
models/model.pkl
metrics.json
```

However, DVC treated `metrics.json` as a regular output file instead of a metric.

The goal was to:

- Remove `metrics.json` from normal outputs
- Register it as a DVC metric
- Disable caching for metric storage
- Re-run the pipeline
- Verify metric visibility

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Existing Train Stage

```yaml
train:
  cmd: python src/models/train.py
  deps:
    - data/processed/train.csv
    - src/models/train.py
  outs:
    - models/model.pkl
    - metrics.json
```

---

## Problem Identified

| Issue | Description |
|---------|-------------|
| Metric treated as output | DVC does not expose values |
| Stored in DVC cache | Not ideal for metric history |
| Metrics unavailable | `dvc metrics show` returns nothing |

---

## Step 1 — Update dvc.yaml

Replace:

```yaml
outs:
  - models/model.pkl
  - metrics.json
```

with:

```yaml
outs:
  - models/model.pkl

metrics:
  - metrics.json:
      cache: false
```

---

## Corrected Train Stage

```yaml
train:
  cmd: python src/models/train.py
  deps:
    - data/processed/train.csv
    - src/models/train.py
  outs:
    - models/model.pkl
  metrics:
    - metrics.json:
        cache: false
```

---

## Why cache: false?

Metrics should:

- remain inside Git
- participate in Git diffs
- support experiment comparisons

instead of being stored in the DVC cache.

---

## Step 2 — Reproduce Pipeline

Run:

```bash
dvc repro
```

### Purpose

Rebuilds the pipeline and updates DVC metadata.

---

## Step 3 — Display Metrics

Run:

```bash
dvc metrics show
```

Expected Output:

```text
Path          accuracy    f1_score
metrics.json  1.0         1.0
```

Values may differ depending on the dataset.

---

## Verification

Verify metric file exists:

```bash
cat metrics.json
```

Example:

```json
{
  "accuracy": 1.0,
  "f1_score": 1.0
}
```

---

## Verify DVC Metrics

```bash
dvc metrics show
```

Expected Result:

```text
accuracy
f1_score
```

are displayed successfully.

---

## Errors & Fixes

### Error 1 — Metrics Not Visible

#### Cause

`metrics.json` was defined as a normal output.

#### Fix

Move it under:

```yaml
metrics:
```

instead of:

```yaml
outs:
```

---

### Error 2 — Metrics Stored in Cache

#### Cause

Metrics defaulted to DVC output behavior.

#### Fix

Use:

```yaml
cache: false
```

to keep metrics versioned through Git.

---

### Error 3 — DVC Metrics Show Empty

#### Cause

Metric file not registered properly.

#### Fix

Declare:

```yaml
metrics:
  - metrics.json:
      cache: false
```

and rerun:

```bash
dvc repro
```

---

## Key Learnings

- DVC supports dedicated metric tracking
- Metrics should be declared separately from outputs
- `cache: false` keeps metrics in Git
- DVC can automatically parse JSON metric files
- Metrics become available through DVC CLI and IDE integrations

---

## Real-World Relevance

DVC metrics are commonly used for:

- Model evaluation
- Experiment tracking
- Performance comparisons
- Hyperparameter tuning
- Continuous ML validation