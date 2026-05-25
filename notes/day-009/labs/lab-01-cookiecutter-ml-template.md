# Lab 01 — Create a Custom ML Project Template with Cookiecutter

## Objective

Fix and standardize a Cookiecutter ML template so new machine learning projects can be generated successfully.

---

## Task Summary

The provided Cookiecutter template contained multiple rendering issues:

- Missing template variables
- Invalid Jinja2 conditional syntax
- Incorrect variable references
- Missing template structure requirements

The goal was to correct the template and generate a working ML project.

---

## Template Directory

```bash
/root/code/mlops-template/
```

---

## Step 1 — Inspect Existing Template

View the existing template configuration:

```bash
cat cookiecutter.json
```

### Existing Configuration

```json
{
    "project_name": "my-ml-project",
    "author": "xFusionCorp",
    "python_version": "3.11"
}
```

---

## Problems Identified

| Problem | Description |
|---------|-------------|
| Missing `ml_framework` variable | Required framework selection missing |
| Invalid Jinja2 syntax | Used `=` instead of `==` |
| Incorrect variable reference | Used `Author` instead of `author` |
| Missing `{% endif %}` | Jinja2 block incomplete |
| Missing required directories | Template structure incomplete |

---

## Step 2 — Correct cookiecutter.json

### Updated Configuration

```json
{
    "project_name": "my-ml-project",
    "author": "xFusionCorp",
    "python_version": "3.11",
    "ml_framework": [
        "sklearn",
        "pytorch",
        "tensorflow"
    ]
}
```

---

## Step 3 — Fix requirements.txt Template

### Incorrect Template

```jinja
{% if cookiecutter.ml_framework = 'sklearn' %}
```

### Problem

Jinja2 conditionals require `==`, not `=`.

---

### Corrected Template

```jinja
{% if cookiecutter.ml_framework == 'sklearn' %}
scikit-learn
{% elif cookiecutter.ml_framework == 'pytorch' %}
torch
{% elif cookiecutter.ml_framework == 'tensorflow' %}
tensorflow
{% endif %}
```

---

## Step 4 — Fix README.md Template

### Incorrect Template

```md
# {{cookiecutter.project_name}}

Created by {{ cookiecutter.Author }}.
```

### Problems

- Incorrect variable casing
- Missing project details

---

### Corrected Template

```md
# {{ cookiecutter.project_name }}

Machine learning project generated for {{ cookiecutter.author }}.

## Python Version

{{ cookiecutter.python_version }}

## ML Framework

{{ cookiecutter.ml_framework }}

## Project Structure

- data/
- models/
- src/
- tests/
```

---

## Step 5 — Verify Template Structure

Required template structure:

```text
{{cookiecutter.project_name}}/
├── README.md
├── requirements.txt
├── data/
├── models/
├── src/
└── tests/
```

---

## Step 6 — Generate a New Project

Run:

```bash
cookiecutter /root/code/mlops-template/ -o /root/code/ --no-input project_name=churn-model ml_framework=sklearn
```

### Purpose

Generates a new ML project from the corrected template.

---

## Verification

Verify generated project:

```bash
tree /root/code/churn-model
```

Verify dependencies:

```bash
cat /root/code/churn-model/requirements.txt
```

Expected Result:

```text
scikit-learn
```

Verify README:

```bash
cat /root/code/churn-model/README.md
```

Expected Result:

- Contains `xFusionCorp`
- Contains project name `churn-model`

---

## Errors & Fixes

### Error 1 — Invalid Jinja2 Conditional Syntax

#### Problem

Used:

```jinja
=
```

instead of:

```jinja
==
```

#### Fix

Updated all conditionals to use proper Jinja2 comparison syntax.

---

### Error 2 — Incorrect Variable Reference

#### Problem

Used:

```jinja
cookiecutter.Author
```

#### Fix

Updated to:

```jinja
cookiecutter.author
```

---

### Error 3 — Missing Template Variable

#### Problem

`ml_framework` variable was missing from `cookiecutter.json`.

#### Fix

Added framework selection list.

---

## Key Learnings

- Cookiecutter automates project scaffolding
- Jinja2 syntax must be precise for rendering
- Template variables enable reusable project generation
- Dynamic dependency generation improves flexibility
- Standardized project templates improve consistency

---

## Real-World Relevance

Cookiecutter templates are widely used in:

- MLOps platforms
- Internal engineering tooling
- Team project scaffolding
- Enterprise ML workflows
- Standardized repository generation