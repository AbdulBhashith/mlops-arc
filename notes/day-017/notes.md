# Notes — Day 017

## Important Concepts

### 1. DVC Experiments

DVC experiments allow testing parameter changes without creating Git commits.

Example:

```bash
dvc exp run -S n_estimators=200
```

---

## 2. Hyperparameter Tuning

Changing:

```yaml
n_estimators
```

affects:

- model complexity
- training performance
- prediction quality

---

## 3. Experiment Tracking

Each experiment stores:

- parameters
- metrics
- artifacts
- execution history

---

## 4. dvc exp show

Command:

```bash
dvc exp show
```

displays:

- experiment names
- parameter values
- metrics

---

## 5. dvc exp apply

Command:

```bash
dvc exp apply <experiment-id>
```

moves the selected experiment into the active workspace.

This updates:

```text
params.yaml
metrics.json
models/model.pkl
```

---

## 6. Experiment Comparison

Typical workflow:

```text
Baseline
    │
    ├── Experiment A
    ├── Experiment B
    └── Experiment C
            │
            ▼
     Select Best Model
            │
            ▼
      Apply Experiment
```

---

## 7. Best Metric Selection

For this lab:

```text
Highest F1 Score Wins
```

because F1 balances:

- precision
- recall

for fraud detection problems.

---

## Troubleshooting Checklist

| Check | Status |
|---------|---------|
| Baseline verified | ✅ |
| Three experiments executed | ✅ |
| Metrics generated | ✅ |
| Experiments visible in DVC | ✅ |
| JSON output verified | ✅ |
| Best experiment identified | ✅ |
| Winning experiment applied | ✅ |
| Model artifact regenerated | ✅ |
| Workspace up to date | ✅ |
|