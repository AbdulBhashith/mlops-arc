# Lab 01 - Create a Python Virtual Environment for ML

## 🎯 Objective

Set up a standardized Python virtual environment for an ML project and install essential machine learning libraries.

---

# 📝 Task

- Create a Python virtual environment named `ml-env`
- Install required ML libraries
- Generate a `requirements.txt` file

---

# 📂 Working Directory

```bash
cd /root/code
```

---

# ⚙️ Create Virtual Environment

```bash
python3 -m venv ml-env
```

---

# ▶️ Activate Virtual Environment

## Linux/macOS

```bash
source ml-env/bin/activate
```

## Windows

```bash
ml-env/Scripts/activate
```

---

# 📦 Install Required Packages

```bash
pip install numpy pandas scikit-learn matplotlib
```

Installed packages:
- numpy
- pandas
- scikit-learn
- matplotlib

---

# 🧾 Generate requirements.txt

```bash
pip freeze > requirements.txt
```

Generated file:
```text
/root/code/requirements.txt
```

---

# ❌ Mistakes Made

## Mistake

Created `requirements.txt` manually before installing packages.

Commands used:

```bash
vi requirements.txt
cat requirements.txt
python3 -m pip install requirements.txt
```

---

# ✅ Fix

Read the question carefully and realized:

- Packages needed to be installed first
- `requirements.txt` should be generated using `pip freeze`

Correct command:

```bash
pip freeze > requirements.txt
```

---

# 🧠 Key Learnings

- Virtual environments isolate dependencies per project
- `pip freeze` captures exact package versions
- Reading the task carefully prevents unnecessary mistakes

---

# 🌍 Real-World Relevance

Virtual environments are essential in MLOps workflows to ensure reproducibility and dependency consistency across environments.