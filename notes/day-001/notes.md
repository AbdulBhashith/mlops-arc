# Notes - Python Virtual Environment

## What is a Virtual Environment?

A virtual environment is an isolated Python environment that allows projects to use separate dependencies without conflicts.

---

# Why Use Virtual Environments?

- Dependency isolation
- Reproducibility
- Prevent version conflicts
- Better project organization

---

# Important Commands

## Create Environment

```bash
python3 -m venv ml-env
```

## Activate Environment

```bash
source ml-env/bin/activate
```

## Install Packages

```bash
pip install <package-name>
```

## Generate requirements.txt

```bash
pip freeze > requirements.txt
```

---

# Important Understanding

`requirements.txt` is usually generated after installing packages using:

```bash
pip freeze
```

This captures exact dependency versions.

---

# Today I Learned

- How to create Python virtual environments
- How to install ML libraries
- How dependency management works
- Importance of `requirements.txt`