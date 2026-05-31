# Notes — Day 015

## Important Concepts

### 1. params.yaml

Stores configurable values used by DVC pipelines.

Example:

```yaml
n_estimators: 100
```

Benefits:

- no code changes required
- reproducible experiments
- centralized configuration

---

## 2. Parameter Tracking

DVC tracks parameters declared under:

```yaml
params:
  - n_estimators
```

inside `dvc.yaml`.

---

## 3. dvc.lock

The lock file stores:

- dependency hashes
- output hashes
- parameter values

Example:

```yaml
params:
  params.yaml:
    n_estimators: 200
```

---

## 4. Selective Stage Reproduction

DVC only re-executes stages affected by changes.

Example:

```text
Parameter Changed
       ↓
Train Stage Re-runs
       ↓
Model Regenerated
```

Upstream stages remain unchanged.

---

## 5. Hyperparameter Management

Common parameters stored in `params.yaml`:

```yaml
n_estimators: 200
max_depth: 10
learning_rate: 0.01
```

This allows experimentation without modifying code.

---

## 6. Reproducible Experiments

By storing parameter values in Git and DVC:

- experiments become reproducible
- results can be compared
- model training is auditable

---

## Troubleshooting Checklist

| Check | Status |
|---------|---------|
| Parameter name corrected | ✅ |
| Pipeline executed successfully | ✅ |
| Model artifact generated | ✅ |
| Parameter updated | ✅ |
| Only train stage re-ran | ✅ |
| `dvc.lock` updated | ✅ |
| Pipeline status clean | ✅ |