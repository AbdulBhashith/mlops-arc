# Notes — Day 018

## Important Concepts

### 1. Git Tags

Tags create fixed reference points.

Example:

```bash
git tag v1.0
```

Useful for:

- Releases
- Rollbacks
- Production versions

---

## 2. Git Branches

Branches allow independent development.

Example:

```text
main
└── v2-improved
```

Each branch can maintain different datasets and models.

---

## 3. DVC Dataset Versioning

DVC tracks datasets using hash-based metadata.

Example:

```text
transactions.csv.dvc
```

Stores:

- file hash
- size
- path

---

## 4. dvc checkout

Command:

```bash
dvc checkout
```

Restores files according to the currently checked-out Git branch.

---

## 5. Dataset Hash Verification

Comparing:

```bash
cat data/raw/transactions.csv.dvc
```

across branches shows different hashes.

Example:

```text
main         -> md5: abc123
v2-improved  -> md5: xyz789
```

---

## 6. Branch-Based ML Development

Typical workflow:

```text
main
 │
 ├── v1.0 Dataset
 │
 └── v2-improved Dataset
          │
          ▼
     Retrained Model
```

---

## 7. Benefits of Dataset Versioning

- Reproducibility
- Rollbacks
- Safer experimentation
- Auditability
- Team collaboration

---

## Troubleshooting Checklist

| Check | Status |
|---------|---------|
| Main branch verified | ✅ |
| v1.0 tag created | ✅ |
| v2-improved branch created | ✅ |
| Dataset updated | ✅ |
| DVC metadata updated | ✅ |
| Pipeline rebuilt | ✅ |
| Commit created | ✅ |
| Dataset restored on main | ✅ |
| DVC checkout successful | ✅ |
| Tag validation passed | ✅ |