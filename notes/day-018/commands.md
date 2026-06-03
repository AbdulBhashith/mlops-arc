# Commands Used — Day 018

## Switch to Main Branch

```bash
git checkout main
```

---

## Create Release Tag

```bash
git tag v1.0
```

---

## Create Improved Dataset Branch

```bash
git checkout -b v2-improved
```

---

## Replace Dataset

```bash
cp data/raw/transactions_v2.csv data/raw/transactions.csv
```

---

## Update DVC Tracking

```bash
dvc add data/raw/transactions.csv
```

---

## Rebuild Pipeline

```bash
dvc repro
```

---

## Commit Changes

```bash
git add .
git commit -m "Use improved dataset and retrain pipeline"
```

---

## Return to Main

```bash
git checkout main
```

---

## Restore Dataset

```bash
dvc checkout
```

---

## Verify Branch

```bash
git branch --show-current
```

---

## Verify Dataset Matches Tag

```bash
git diff v1.0 -- data/raw/transactions.csv.dvc
```

---

## Compare Dataset Hashes

```bash
cat data/raw/transactions.csv.dvc
```