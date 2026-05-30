# Day-014: Create a DVC Pipeline for Data Processing

## Overview

This lab focused on building a reproducible DVC pipeline for data processing in the `fraud-detection` project.

The task involved:

- Reviewing an incorrect `dvc.yaml`
- Fixing stage commands and outputs
- Defining proper stage dependencies
- Creating a complete multi-stage DVC pipeline
- Running pipeline reproduction successfully

---

## Technologies Used

- DVC
- Python
- YAML
- Git
- MLOps

---

## Skills Practiced

- DVC pipeline creation
- Data pipeline orchestration
- Dependency management
- Reproducible ML workflows
- Pipeline troubleshooting

---

## Lab Files

| File | Description |
|------|-------------|
| `labs/lab-01-create-dvc-pipeline.md` | Detailed lab walkthrough |
| `commands.md` | Important commands used |
| `notes.md` | Key learnings and troubleshooting notes |

---

## Outcome

Successfully corrected the DVC pipeline and executed all stages end-to-end using:

```bash
dvc repro
```

The pipeline now contains:

1. Data Processing Stage
2. Data Splitting Stage

with proper dependency tracking and reproducible outputs.