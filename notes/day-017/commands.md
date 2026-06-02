# Commands Used — Day 017

## Navigate to Project

```bash
cd /root/code/fraud-detection
```

---

## Check Baseline Parameter

```bash
cat params.yaml
```

---

## Run Experiment 1

```bash
dvc exp run -S n_estimators=50
```

---

## Run Experiment 2

```bash
dvc exp run -S n_estimators=200
```

---

## Run Experiment 3

```bash
dvc exp run -S n_estimators=500
```

---

## Show Experiment Results

```bash
dvc exp show
```

---

## Show Experiments in JSON Format

```bash
dvc exp show --json
```

---

## Apply Best Experiment

```bash
dvc exp apply <experiment-id>
```

---

## Verify Parameters

```bash
cat params.yaml
```

---

## Verify Metrics

```bash
cat metrics.json
```

---

## Verify Model Artifact

```bash
ls -l models/model.pkl
```

---

## Verify Pipeline State

```bash
dvc status
```