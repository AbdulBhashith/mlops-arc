# Notes — Day 011

## Important Concepts

### 1. DVC Dataset Tracking

DVC tracks datasets using lightweight metadata files instead of storing large datasets directly in Git.

---

## 2. .dvc Pointer Files

Example:

```text
transactions.csv.dvc
```

The `.dvc` file stores:

- dataset hash
- file path
- tracking metadata

---

## 3. Git vs DVC Responsibilities

| Tool | Tracks |
|------|---------|
| Git | source code and DVC metadata |
| DVC | datasets and ML artifacts |

---

## 4. git rm --cached

Command:

```bash
git rm --cached <file>
```

removes a file from Git tracking while keeping it on disk.

---

## 5. data/raw/.gitignore

DVC automatically updates `.gitignore` to prevent datasets from being committed to Git.

Example:

```text
/transactions.csv
```

---

## 6. Benefits of DVC

DVC helps teams:

- manage large datasets
- version ML artifacts
- reproduce experiments
- collaborate efficiently
- avoid bloated Git repositories

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Dataset removed from Git tracking | ✅ |
| Dataset preserved locally | ✅ |
| `.dvc` pointer file created | ✅ |
| `.gitignore` updated | ✅ |
| Changes committed successfully | ✅ |
| Dataset tracked by DVC | ✅ |