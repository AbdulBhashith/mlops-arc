# Notes — Day 019

## Important Concepts

### 1. DVC Pipelines

DVC pipelines connect data processing stages into a reproducible workflow.

Example:

```text
ingest
 ↓
validate
 ↓
preprocess
 ↓
train
 ↓
evaluate
```

---

## 2. Parameter Dependencies

Parameters are tracked through:

```yaml
params.yaml
```

Example:

```yaml
n_estimators: 100
max_depth: 5
test_size: 0.2
random_seed: 42
```

Changes automatically trigger stage re-execution.

---

## 3. Metrics vs Reports

### Metrics

Used for:

```text
accuracy
f1_score
precision
recall
```

Stored as:

```yaml
metrics:
```

---

### Reports

Used for:

```text
evaluation summaries
analysis outputs
```

Stored as:

```yaml
outs:
```

with:

```yaml
cache: false
```

---

## 4. DVC Remote Storage

SeaweedFS stores:

```text
models
datasets
artifacts
```

outside Git.

Benefits:

- Reduced repository size
- Centralized artifact storage
- Team collaboration

---

## 5. Release Tags

Git tags mark stable versions.

Example:

```bash
git tag v1.0
```

Used for:

- Releases
- Rollbacks
- Production deployments

---

## 6. Reproducibility

Running:

```bash
dvc repro
```

recreates:

- datasets
- models
- metrics
- reports

from tracked dependencies.

---

## 7. Production MLOps Workflow

```text
Raw Data
    ↓
Validation
    ↓
Preprocessing
    ↓
Training
    ↓
Evaluation
    ↓
Remote Storage
    ↓
Tagged Release
```

---

## Troubleshooting Checklist

| Check | Status |
|---------|---------|
| Preprocess output fixed | ✅ |
| Train stage added | ✅ |
| Evaluate stage added | ✅ |
| Parameters tracked | ✅ |
| Metrics registered | ✅ |
| Evaluation report generated | ✅ |
| Pipeline reproduced | ✅ |
| DVC push successful | ✅ |
| Git commit created | ✅ |
| Release tagged | ✅ |
| SeaweedFS artifacts uploaded | ✅ |
| Workspace clean | ✅ |