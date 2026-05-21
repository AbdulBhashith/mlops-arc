# Commands Used — Day 005

## Navigate to Project Directory

```bash
cd /root/code/fraud-detection
```

---

## Run Existing Workflow

```bash
make all
```

---

## Create Virtual Environment

```bash
python3 -m venv mlops-venv
```

---

## Install Dependencies

```bash
./mlops-venv/bin/pip install -r requirements.txt
```

---

## Run Data Processing

```bash
python src/data/process_data.py
```

---

## Run Model Training

```bash
python src/models/train.py
```

---

## Run Tests

```bash
pytest tests/
```

---

## Remove Python Cache Files

```bash
find . -type d -name "__pycache__" -exec rm -rf {} +
```

---

## Remove pytest Cache

```bash
rm -rf .pytest_cache
```

---

## Clear Models Directory

```bash
rm -rf models/*
```