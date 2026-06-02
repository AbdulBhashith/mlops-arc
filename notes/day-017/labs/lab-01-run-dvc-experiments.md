# Lab 01 — Run and Compare DVC Experiments

## Objective

Run multiple DVC experiments using different hyperparameter values, compare model performance, and promote the best experiment to the workspace.

---

## Task Summary

The project already contained:

- A parameterized DVC pipeline
- Tracked metrics
- A baseline model

The goal was to:

1. Run three experiments
2. Modify `n_estimators`
3. Compare experiment metrics
4. Select the highest `f1_score`
5. Apply the winning experiment

---

## Project Directory

```bash
/root/code/fraud-detection
```

---

## Step 1 — Verify Baseline Parameters

Check the current parameter value:

```bash
cat params.yaml
```

Expected:

```yaml
n_estimators: 100
```

---

## Step 2 — Run Three Experiments

Execute:

```bash
dvc exp run -S n_estimators=50
```

```bash
dvc exp run -S n_estimators=200
```

```bash
dvc exp run -S n_estimators=500
```

### Purpose

Each command:

- creates an isolated experiment
- trains a new model
- generates a new metrics.json
- stores results in DVC experiment history

---

## Step 3 — View Experiment Results

Run:

```bash
dvc exp show
```

Expected structure:

```text
workspace
main
├── exp-1
├── exp-2
└── exp-3
```

Each experiment displays:

- parameter values
- accuracy
- f1_score

---

## Step 4 — Verify Experiment Metadata

Run:

```bash
dvc exp show --json
```

### Purpose

Ensures all experiment records are stored correctly.

Expected:

```json
{
  "workspace": {},
  "exp-1": {},
  "exp-2": {},
  "exp-3": {}
}
```

---

## Step 5 — Identify Best Experiment

Run:

```bash
dvc exp show
```

Compare:

```text
n_estimators    f1_score
50              0.89
200             0.92
500             0.83
```

Example winner:

```text
n_estimators = 200
```

because it achieved the highest F1 score.

---

## Step 6 — Apply Winning Experiment

Apply the selected experiment:

```bash
dvc exp apply <experiment-id>
```

Example:

```bash
dvc exp apply f806ae4
```

### Purpose

Moves the experiment into the active workspace.

---

## Step 7 — Verify Workspace State

Check parameters:

```bash
cat params.yaml
```

Expected:

```yaml
n_estimators: 200
```

Check metrics:

```bash
cat metrics.json
```

Example:

```json
{
  "accuracy": 0.94,
  "f1_score": 0.92
}
```

---

## Step 8 — Verify Model Artifact

Run:

```bash
ls -l models/model.pkl
```

Expected:

```text
models/model.pkl
```

exists and is regenerated.

---

## Step 9 — Final Validation

Run:

```bash
dvc exp show
```

```bash
dvc exp show --json
```

```bash
dvc status
```

Expected:

```text
Data and pipelines are up to date
```

---

## Errors & Fixes

### Error 1 — Experiments Not Visible

#### Cause

Experiment execution failed.

#### Fix

Run:

```bash
dvc exp run -S n_estimators=<value>
```

again and verify:

```bash
dvc exp show
```

---

### Error 2 — Missing Experiment Records

#### Cause

Experiments were removed accidentally.

#### Fix

Do NOT run:

```bash
dvc exp remove
dvc exp gc
dvc exp prune
```

before validation.

---

### Error 3 — Wrong Experiment Applied

#### Cause

Applied an experiment without checking metrics.

#### Fix

Compare:

```bash
dvc exp show
```

and choose the highest:

```text
f1_score
```

---

## Key Learnings

- DVC Experiments allow hyperparameter tuning without changing Git history
- Each experiment stores metrics and parameters separately
- DVC tracks experiment metadata automatically
- Best-performing experiments can be promoted instantly
- Experiment comparison improves model selection workflows

---

## Real-World Relevance

DVC experiments are commonly used for:

- Hyperparameter optimization
- Model benchmarking
- Experiment tracking
- Performance comparison
- Production MLOps pipelines