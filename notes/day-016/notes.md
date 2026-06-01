# Notes — Day 016

## Important Concepts

### 1. DVC Metrics

DVC metrics are files that contain model evaluation results.

Example:

```json
{
  "accuracy": 0.95,
  "f1_score": 0.93
}
```

---

## 2. Metrics vs Outputs

| Type | Purpose |
|--------|----------|
| outs | Stores generated artifacts |
| metrics | Stores evaluation results |

Examples:

```yaml
outs:
  - models/model.pkl
```

```yaml
metrics:
  - metrics.json
```

---

## 3. cache: false

Using:

```yaml
cache: false
```

keeps metric files:

- inside Git
- available for diffs
- easy to review

instead of storing them in the DVC cache.

---

## 4. dvc metrics show

Command:

```bash
dvc metrics show
```

extracts metric values directly from tracked files.

Example output:

```text
accuracy
f1_score
```

---

## 5. JSON Metrics

DVC automatically parses structured JSON metrics.

Example:

```json
{
  "accuracy": 0.98,
  "f1_score": 0.97
}
```

---

## 6. Experiment Tracking

Metrics enable:

- experiment comparison
- performance monitoring
- model validation
- reproducible evaluations

---

## Troubleshooting Checklist

| Check | Status |
|---------|---------|
| Metric removed from outs | ✅ |
| Metric added under metrics | ✅ |
| cache: false configured | ✅ |
| Pipeline reproduced | ✅ |
| metrics.json generated | ✅ |
| dvc metrics show working | ✅ |
| Accuracy visible | ✅ |
| F1 Score visible | ✅ |