# Day-017: Run and Compare DVC Experiments

## Overview

This lab focused on using DVC Experiments to compare multiple model training runs with different hyperparameter values.

The task involved:

- Running multiple DVC experiments
- Testing different values of `n_estimators`
- Comparing experiment metrics
- Identifying the best-performing model
- Applying the winning experiment to the workspace

---

## Technologies Used

- DVC
- Python
- Scikit-Learn
- Random Forest
- MLOps

---

## Skills Practiced

- DVC experiment management
- Hyperparameter tuning
- Experiment comparison
- Model selection
- Reproducible ML workflows

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-run-dvc-experiments.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully executed three DVC experiments using different values for:

```yaml
n_estimators
```

Compared experiment metrics and promoted the best-performing experiment to the tracked workspace.

The selected experiment became the active project state, including:

- params.yaml
- metrics.json
- models/model.pkl

---