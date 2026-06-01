# Day-016: Track ML Metrics with DVC

## Overview

This lab focused on configuring DVC to track machine learning metrics generated during model training.

The task involved:

- Reviewing the existing DVC pipeline
- Converting `metrics.json` from a regular output into a DVC metric
- Disabling caching for metric tracking
- Reproducing the pipeline
- Displaying model metrics through DVC

---

## Technologies Used

- DVC
- Python
- Scikit-Learn
- JSON
- MLOps

---

## Skills Practiced

- DVC metrics tracking
- Pipeline configuration
- Experiment monitoring
- Model evaluation
- Reproducible ML workflows

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-track-ml-metrics.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully configured DVC to recognize:

```text
metrics.json
```

as a tracked metric file.

Metrics can now be viewed using:

```bash
dvc metrics show
```

and surfaced directly in the DVC extension's Metrics panel.

Example metrics:

```json
{
  "accuracy": 1.0,
  "f1_score": 1.0
}
```