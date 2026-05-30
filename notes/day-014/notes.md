# Notes — Day 014

## Important Concepts

### 1. DVC Pipelines

DVC pipelines automate reproducible data workflows.

Each stage contains:

- command (`cmd`)
- dependencies (`deps`)
- outputs (`outs`)

---

## 2. Dependencies

Dependencies are files required for a stage to run.

Example:

```yaml
deps:
  - data/raw/transactions.csv
  - src/data/process_data.py
```

If either changes, DVC knows the stage is outdated.

---

## 3. Outputs

Outputs are files produced by a stage.

Example:

```yaml
outs:
  - data/processed/clean_transactions.csv
```

DVC tracks output hashes to determine reproducibility.

---

## 4. dvc repro

Command:

```bash
dvc repro
```

Purpose:

- Executes pipeline stages
- Rebuilds outdated outputs
- Maintains reproducibility

---

## 5. dvc status

Command:

```bash
dvc status
```

Checks:

- stale stages
- changed dependencies
- missing outputs

---

## 6. Pipeline Chaining

Outputs from one stage can become dependencies of another stage.

Example:

```text
Raw Data
    ↓
Processing
    ↓
Clean Data
    ↓
Train/Test Split
```

This creates a reproducible dependency graph.

---

## Troubleshooting Checklist

| Check | Status |
|--------|--------|
| Correct process script configured | ✅ |
| Correct output file configured | ✅ |
| Split stage dependency added | ✅ |
| Pipeline reproduced successfully | ✅ |
| Outputs generated | ✅ |
| `dvc status` clean | ✅ |