# Lab 01 — Fix Broken uv Lockfile Specification

## Objective

Fix invalid Python dependency specifications and generate a reproducible lockfile using `uv`.

---

## Task Summary

The provided `requirements.in` file contained invalid dependency specifications that prevented lockfile generation.

The goal was to:

- Inspect the dependency file
- Identify incorrect package names or version formats
- Correct the specifications
- Compile dependencies into a pinned `requirements.txt`

---

## Environment Details

| Component | Purpose |
|-----------|---------|
| `requirements.in` | Source dependency file |
| `requirements.txt` | Generated lockfile |
| `uv` | Dependency management tool |

---

## Step 1 — Inspect Dependency File

View the existing dependency file:

```bash
cat requirements.in
```

### Purpose

Checks the dependency specifications for invalid entries.

---

## Step 2 — Identify Invalid Specifications

Example issues found:

```text
numppy==1.26
pandas=>2.0
```

### Problems

| Dependency | Issue |
|------------|------|
| `numppy` | Incorrect package name |
| `pandas=>2.0` | Invalid version syntax |

---

## Step 3 — Correct Dependency File

Updated `requirements.in`:

```txt
numpy==1.26
pandas>=2.0
```

### Purpose

Fixes invalid package names and version constraints.

---

## Step 4 — Generate Lockfile

Run the following command:

```bash
uv pip compile requirements.in -o requirements.txt
```

### Purpose

Compiles dependencies into a reproducible lockfile with pinned versions.

---

## Verification

Verify the lockfile was generated:

```bash
cat requirements.txt
```

Expected Result:

- Fully resolved package versions
- Reproducible dependency list

---

## Errors & Fixes

### Error 1 — Invalid Package Name

#### Error

```text
No matching distribution found
```

#### Cause

Incorrect package name in `requirements.in`.

#### Fix

Corrected the dependency name.

---

### Error 2 — Invalid Version Constraint

#### Error

```text
Invalid requirement syntax
```

#### Cause

Incorrect version operator format.

#### Fix

Updated:

```txt
pandas>=2.0
```

---

## Key Learnings

- Dependency files must follow valid Python package syntax
- Version constraints are important for compatibility
- Lockfiles improve reproducibility across environments
- `uv` provides fast dependency resolution and compilation

---

## Real-World Relevance

Dependency lockfiles are critical in:

- MLOps pipelines
- CI/CD systems
- Production deployments
- Docker image reproducibility
- Team collaboration environments