# Lab 01 — Package an ML Project as an Installable Python Package

## Objective

Correct the Python packaging configuration and build the `fraud-detection` project as an installable wheel package.

---

## Task Summary

The provided `pyproject.toml` contained incorrect package metadata and missing build system configuration.

The goal was to:

- Configure the build system correctly
- Match the package name with the module structure
- Define dependencies
- Set the required Python version
- Build the project successfully

---

## Project Directory

```bash
/root/code/fraud-detection/
```

---

## Existing Configuration

```toml
[project]
name = "fraud-detection"
version = "0.0.1"
description = "Fraud detection model for xFusionCorp Industries"
requires-python = ">=3.8"
dependencies = []

[tool.setuptools.packages.find]
where = ["src"]
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| Missing `[build-system]` | Required for package builds |
| Incorrect package name | Must match module path |
| Wrong version | Required version is `0.1.0` |
| Incorrect Python version | Must be `>=3.10` |
| Missing dependencies | Required packages not listed |

---

## Step 1 — Correct pyproject.toml

### Updated Configuration

```toml
[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "fraud_detection"
version = "0.1.0"
description = "Fraud detection model for xFusionCorp Industries"
requires-python = ">=3.10"
dependencies = [
    "scikit-learn",
    "pandas",
    "numpy",
]

[tool.setuptools.packages.find]
where = ["src"]
```

---

## Step 2 — Build the Package

Navigate to the project directory:

```bash
cd /root/code/fraud-detection
```

Run the build command:

```bash
python3 -m build
```

### Purpose

Builds:

- source distribution (`sdist`)
- wheel distribution (`.whl`)

---

## Verification

Check generated build artifacts:

```bash
ls dist/
```

Expected Result:

```text
fraud_detection-0.1.0-py3-none-any.whl
```

---

## Errors & Fixes

### Error 1 — Missing Build System

#### Problem

The package could not build without a valid `[build-system]` section.

#### Fix

Added:

```toml
[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.build_meta"
```

---

### Error 2 — Incorrect Distribution Name

#### Problem

The package name did not match the module path under `src/`.

#### Fix

Updated:

```toml
name = "fraud_detection"
```

---

### Error 3 — Missing Dependencies

#### Problem

Required runtime dependencies were not declared.

#### Fix

Added:

```toml
dependencies = [
    "scikit-learn",
    "pandas",
    "numpy",
]
```

---

## Key Learnings

- `pyproject.toml` is the modern standard for Python packaging
- Wheel files provide installable binary distributions
- Package names should match Python module paths
- Dependencies should be explicitly declared
- Build systems define how packages are created

---

## Real-World Relevance

Python packaging is essential in:

- MLOps deployments
- Internal ML libraries
- CI/CD pipelines
- Production ML services
- Reusable enterprise tooling