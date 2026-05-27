# Commands Used — Day 011

## Navigate to Repository

```bash
cd /root/code/fraud-detection
```

---

## Remove Dataset from Git Tracking

```bash
git rm --cached data/raw/transactions.csv
```

---

## Track Dataset with DVC

```bash
dvc add data/raw/transactions.csv
```

---

## Stage DVC Metadata Files

```bash
git add data/raw/transactions.csv.dvc data/raw/.gitignore
```

---

## Commit Dataset Tracking Changes

```bash
git commit -m "Track transactions dataset with DVC"
```

---

## Verify Git Status

```bash
git status
```

---

## Verify DVC Status

```bash
dvc status
```