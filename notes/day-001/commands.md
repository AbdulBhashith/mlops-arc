# Commands Used - Day 001

## Navigate to Working Directory

```bash
cd /root/code
```

---

# Create Virtual Environment

```bash
python3 -m venv ml-env
```

Creates an isolated Python environment.

---

# Activate Virtual Environment

## Linux/macOS

```bash
source ml-env/bin/activate
```

## Windows

```bash
ml-env/Scripts/activate
```

Activates the virtual environment.

---

# Install Packages

```bash
pip install numpy pandas scikit-learn matplotlib
```

Installs required ML libraries.

---

# Generate requirements.txt

```bash
pip freeze > requirements.txt
```

Exports installed package versions to a requirements file.