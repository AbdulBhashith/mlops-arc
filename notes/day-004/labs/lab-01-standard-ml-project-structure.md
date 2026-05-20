# Lab 01 — Create a Standard ML Project Structure

## Objective

Standardize an existing machine learning project structure to match xFusionCorp Industries development conventions.

---

## Task Summary

The provided project structure did not fully match the required company standards.

The goal was to:

- Inspect the existing project
- Create missing directories
- Rename incorrect folders
- Add Python package initialization files
- Update dependencies
- Correct the README file

---

## Required Final Structure

```text
fraud-detection/
├── data/
│   ├── raw/
│   └── processed/
├── models/
├── notebooks/
├── src/
│   ├── data/
│   ├── features/
│   ├── models/
│   └── utils/
├── tests/
├── configs/
├── requirements.txt
└── README.md
```

---

## Step 1 — Inspect Existing Project

Navigate into the project directory:

```bash
cd /root/code/fraud-detection
```

Check the current structure:

```bash
tree
```

### Purpose

Helps identify missing folders and incorrect naming conventions.

---

## Step 2 — Rename Incorrect Directories

Some folders were incorrectly named:

| Incorrect | Correct |
|-----------|---------|
| `feature/` | `features/` |
| `util/` | `utils/` |

Rename directories:

```bash
mv src/feature src/features
mv src/util src/utils
```

---

## Step 3 — Create Missing Directories

Create required directories:

```bash
mkdir -p data/raw
mkdir -p data/processed
mkdir -p tests
mkdir -p configs
```

### Purpose

Ensures the project matches the required ML project structure.

---

## Step 4 — Add Python Package Initialization Files

Create `__init__.py` files inside all `src/` subdirectories:

```bash
touch src/data/__init__.py
touch src/features/__init__.py
touch src/models/__init__.py
touch src/utils/__init__.py
```

### Purpose

Allows Python to recognize these directories as packages.

---

## Step 5 — Update requirements.txt

Update dependencies:

```txt
scikit-learn
pandas
numpy
mlflow
```

### Purpose

Defines the required Python dependencies for the project.

---

## Step 6 — Update README.md

Ensure the README starts with:

```md
# fraud-detection
```

### Purpose

Matches the required project naming convention.

---

## Verification

Verify the final structure:

```bash
tree
```

Verify dependencies:

```bash
cat requirements.txt
```

Verify README heading:

```bash
head -n 1 README.md
```

---

## Errors & Fixes

### Error 1 — Incorrect Folder Names

#### Problem

Some folders did not follow the standard naming convention.

#### Fix

Renamed:

```bash
mv src/feature src/features
mv src/util src/utils
```

---

### Error 2 — Missing Package Initialization Files

#### Problem

Python would not recognize subdirectories as packages.

#### Fix

Added:

```bash
touch src/data/__init__.py
touch src/features/__init__.py
touch src/models/__init__.py
touch src/utils/__init__.py
```

---

## Key Learnings

- Standard project structures improve maintainability
- `__init__.py` files are important for Python package recognition
- Organized ML repositories improve collaboration
- Consistent naming conventions reduce confusion
- Proper dependency tracking helps reproducibility

---

## Real-World Relevance

Standard ML project structures are widely used in:

- Production ML systems
- MLOps pipelines
- Team collaboration projects
- CI/CD workflows
- Enterprise machine learning platforms