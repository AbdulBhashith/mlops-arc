# Notes — Day 010

## Important Concepts

### 1. DVC (Data Version Control)

DVC is an MLOps tool used for:

- dataset versioning
- model artifact tracking
- ML pipeline reproducibility
- experiment management

---

## 2. DVC Initialization

Command:

```bash
dvc init
```

creates:

```text
.dvc/
.dvcignore
```

inside the repository.

---

## 3. .dvc Directory

The `.dvc/` directory stores:

- DVC configuration
- cache settings
- pipeline metadata
- internal tracking files

---

## 4. .dvcignore

Works similarly to `.gitignore`.

Used to exclude files or directories from DVC tracking.

---

## 5. Git + DVC Workflow

Git tracks:

- source code
- DVC metadata

DVC tracks:

- datasets
- model files
- large artifacts

---

## 6. Reproducible ML Pipelines

DVC helps teams reproduce:

- experiments
- training pipelines
- model outputs
- data processing steps

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Inside Git repository | ✅ |
| DVC initialized successfully | ✅ |
| `.dvc/` directory created | ✅ |
| `.dvcignore` created | ✅ |
| Files staged in Git | ✅ |
| Commit created successfully | ✅ |
```