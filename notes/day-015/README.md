# Day-015: Parameterize a DVC Pipeline

## Overview

This lab focused on parameterizing a DVC pipeline using `params.yaml` to manage model hyperparameters without modifying source code.

The task involved:

- Fixing a parameter mismatch between `dvc.yaml` and `params.yaml`
- Running the complete DVC pipeline successfully
- Updating a hyperparameter value
- Demonstrating DVC's parameter tracking capabilities
- Verifying selective stage re-execution

---

## Technologies Used

- DVC
- Python
- YAML
- Machine Learning
- MLOps

---

## Skills Practiced

- DVC parameter management
- Pipeline reproducibility
- Hyperparameter tracking
- Experiment management
- Dependency-based pipeline execution

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-parameterize-dvc-pipeline.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully parameterized the training pipeline using `params.yaml`.

Verified that:

- DVC detects parameter changes
- Only affected stages re-run
- `dvc.lock` records parameter values
- Model artifacts are regenerated automatically