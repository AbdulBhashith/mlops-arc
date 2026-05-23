# Notes — Day 007

## Important Concepts

### 1. pyproject.toml

`pyproject.toml` is the modern configuration file for Python packaging and build systems.

It defines:

- project metadata
- dependencies
- build configuration
- tooling settings

---

## 2. Build System Configuration

The `[build-system]` section tells Python how to build the package.

Example:

```toml
[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.build_meta"
```

---

## 3. Wheel Packages

A wheel (`.whl`) is a built Python distribution format.

Benefits:

- faster installation
- reproducible builds
- easier deployment

---

## 4. Package Naming

The distribution name should match the module structure.

Example:

```text
src/fraud_detection/
```

Corresponding package name:

```toml
name = "fraud_detection"
```

---

## 5. Dependency Declaration

Dependencies required by the project must be listed explicitly.

Example:

```toml
dependencies = [
    "scikit-learn",
    "pandas",
    "numpy",
]
```

---

## 6. Python Version Requirements

The `requires-python` field defines supported Python versions.

Example:

```toml
requires-python = ">=3.10"
```

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Build system configured | ✅ |
| Package name corrected | ✅ |
| Version updated | ✅ |
| Python version updated | ✅ |
| Dependencies added | ✅ |
| Wheel package generated | ✅ |
```