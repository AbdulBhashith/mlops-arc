# Commands Used — Day 019

## Navigate to Project

```bash
cd /root/code/ml-pipeline
```

---

## Review Pipeline

```bash
cat dvc.yaml
```

---

## Inspect Preprocess Script

```bash
cat scripts/preprocess.py
```

---

## Copy Training Script

```bash
cp scripts-staging/train.py scripts/train.py
```

---

## Copy Evaluation Script

```bash
cp scripts-staging/evaluate.py scripts/evaluate.py
```

---

## Verify Parameters

```bash
cat params.yaml
```

---

## Add Train Stage

```bash
dvc stage add \
-n train \
-d scripts/train.py \
-d data/processed/clean.csv \
-p n_estimators,max_depth,test_size,random_seed \
-o models/model.pkl \
-o data/processed/test_split.csv \
-M metrics.json \
python scripts/train.py
```

---

## Add Evaluate Stage

```bash
dvc stage add \
-n evaluate \
-d scripts/evaluate.py \
-d models/model.pkl \
-d data/processed/test_split.csv \
-O reports/evaluation.json \
python scripts/evaluate.py
```

---

## Run Pipeline

```bash
dvc repro
```

---

## Display Metrics

```bash
dvc metrics show
```

---

## Verify Pipeline Status

```bash
dvc status
```

---

## Push Artifacts

```bash
dvc push
```

---

## Commit Changes

```bash
git add .
git commit -m "Complete fraud detection DVC pipeline release v1.0"
```

---

## Create Release Tag

```bash
git tag v1.0
```

---

## Verify Release

```bash
git describe --tags
```