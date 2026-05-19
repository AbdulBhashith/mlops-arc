# Notes — Day 003

## Important Concepts

### 1. Dependency Specification Files

`requirements.in` contains high-level package requirements.

Example:

```txt
numpy==1.26
pandas>=2.0
```

---

## 2. Lockfiles

`requirements.txt` stores fully resolved package versions for reproducible environments.

---

## 3. Version Constraints

Common version operators:

| Operator | Meaning |
|----------|---------|
| `==` | Exact version |
| `>=` | Minimum version |
| `<=` | Maximum version |

---

## 4. uv Package Manager

`uv` is a fast Python package and dependency management tool.

Benefits:

- Faster dependency resolution
- Reproducible environments
- Lockfile generation
- Better performance than traditional tooling

---

## 5. Reproducibility in MLOps

Pinned dependencies help ensure:

- Consistent deployments
- Stable pipelines
- Reliable CI/CD workflows
- Reduced environment drift

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Dependency names valid | ✅ |
| Version syntax correct | ✅ |
| Lockfile generated successfully | ✅ |
| Dependencies resolved properly | ✅ |
```