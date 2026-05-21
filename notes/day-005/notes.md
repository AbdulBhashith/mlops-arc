# Notes — Day 005

## Important Concepts

### 1. Makefile Automation

A Makefile automates repetitive development tasks.

Common ML workflow tasks include:

- environment setup
- data processing
- model training
- testing
- cleanup

---

## 2. .PHONY Targets

`.PHONY` tells `make` that targets are commands, not files.

Example:

```Makefile
.PHONY: setup data train test clean all
```

Without `.PHONY`, Make may skip commands if matching filenames exist.

---

## 3. Tab Indentation in Makefiles

Makefiles require real tab characters for recipes.

Incorrect:

```Makefile
data:
    python script.py
```

Correct:

```Makefile
data:
	python script.py
```

---

## 4. Workflow Sequencing

The `all` target orchestrates the complete ML pipeline.

Example:

```Makefile
all: setup data train test
```

---

## 5. Cleanup Automation

Cleaning cache and generated artifacts helps maintain a clean environment.

Important cleanup tasks:

- remove `__pycache__`
- remove `.pytest_cache`
- clear model artifacts

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| `.PHONY` targets added | ✅ |
| Tab indentation fixed | ✅ |
| `data` target included in `all` | ✅ |
| Cleanup commands corrected | ✅ |
| `make all` runs successfully | ✅ |