# Lab 01 — Parameterize a DVC Pipeline

## Objective

Fix parameter wiring between `dvc.yaml` and `params.yaml`, then demonstrate how DVC tracks parameter changes and selectively reproduces pipeline stages.

---

## Task Summary

The project already contained a three-stage DVC pipeline:

```text
process_data
     ↓
split_data
     ↓
train
```

The train stage was configured to track:

```yaml
params:
  - n_estimators
```

However, `params.yaml` contained a mismatched parameter name, causing `dvc repro` to fail.

The goal was to:

- Correct the parameter definition
- Execute the pipeline successfully
- Modify the parameter value
- Verify that only the training stage re-runs

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Existing Configuration

### params.yaml

```yaml
n_estimator: 100
```

### dvc.yaml

```yaml
train:
  cmd: python src/models/train.py
  deps:
    - data/processed/train.csv
    - src/models/train.py
  params:
    - n_estimators
  outs:
    - models/model.pkl
```

---

## Problem Identified

| File | Issue |
|--------|--------|
| params.yaml | Parameter name does not match |
| dvc.yaml | Expects `n_estimators` |
| params.yaml | Contains `n_estimator` |

DVC requires exact parameter name matching.

---

## Step 1 — Fix params.yaml

Update:

```yaml
n_estimator: 100
```

to:

```yaml
n_estimators: 100
```

---

## Correct Configuration

### params.yaml

```yaml
n_estimators: 100
```

---

## Step 2 — Run the Pipeline

Execute:

```bash
cd /root/code/fraud-detection

dvc repro
```

### Purpose

Runs the entire pipeline and creates all required outputs.

---

## Expected Outputs

```text
data/processed/clean_transactions.csv
data/processed/train.csv
data/processed/test.csv
models/model.pkl
```

---

## Step 3 — Demonstrate Parameter Tracking

Modify:

```yaml
n_estimators: 100
```

to:

```yaml
n_estimators: 200
```

---

## Step 4 — Reproduce the Pipeline Again

Run:

```bash
dvc repro
```

---

## Expected Behavior

### Stage Execution

| Stage | Result |
|---------|---------|
| process_data | Skipped |
| split_data | Skipped |
| train | Re-executed |

DVC detects that only the tracked parameter changed.

---

## Verify dvc.lock

Check:

```bash
cat dvc.lock
```

Expected section:

```yaml
train:
  params:
    params.yaml:
      n_estimators: 200
```

---

## Verify Changes

Run:

```bash
git diff params.yaml dvc.lock
```

Expected output:

```diff
-n_estimators: 100
+n_estimators: 200
```

Along with updates inside:

```text
dvc.lock
```

---

## Verification

Check pipeline status:

```bash
dvc status
```

Expected Result:

```text
Data and pipelines are up to date.
```

---

## Errors & Fixes

### Error 1 — Missing Parameter

#### Problem

```yaml
n_estimator
```

did not match:

```yaml
n_estimators
```

required by DVC.

#### Fix

Updated:

```yaml
n_estimators: 100
```

---

### Error 2 — Pipeline Reproduction Failure

#### Cause

DVC could not resolve the parameter specified in:

```yaml
params:
  - n_estimators
```

#### Fix

Added the matching key inside:

```yaml
params.yaml
```

---

## Key Learnings

- DVC tracks parameters independently from source code
- Parameters are defined in `params.yaml`
- Parameter names must match exactly
- `dvc.lock` records parameter values used during execution
- DVC re-runs only affected stages when parameters change

---

## Real-World Relevance

Parameterized DVC pipelines are commonly used for:

- Hyperparameter tuning
- Experiment tracking
- Model optimization
- Reproducible ML workflows
- Production MLOps pipelines