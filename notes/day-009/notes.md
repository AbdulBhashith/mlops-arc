# Notes — Day 009

## Important Concepts

### 1. Cookiecutter

Cookiecutter is a project templating tool used to generate reusable project structures.

Benefits:

- standardized repositories
- reusable templates
- faster project setup
- consistent engineering practices

---

## 2. cookiecutter.json

Defines template variables and defaults.

Example:

```json
{
    "project_name": "my-ml-project",
    "author": "xFusionCorp"
}
```

---

## 3. Jinja2 Template Syntax

Cookiecutter uses Jinja2 templating.

Correct conditional syntax:

```jinja
{% if variable == 'value' %}
```

---

## 4. Dynamic Dependency Generation

Dependencies can change dynamically based on selected frameworks.

Example:

| Framework | Dependency |
|-----------|------------|
| sklearn | scikit-learn |
| pytorch | torch |
| tensorflow | tensorflow |

---

## 5. Template Variables

Variables can be referenced using:

```jinja
{{ cookiecutter.variable_name }}
```

Example:

```jinja
{{ cookiecutter.project_name }}
```

---

## 6. Standard ML Project Structure

Reusable project structures improve:

- maintainability
- onboarding
- collaboration
- scalability

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| `ml_framework` variable added | ✅ |
| Jinja2 syntax corrected | ✅ |
| README variables fixed | ✅ |
| Template structure valid | ✅ |
| Project generated successfully | ✅ |
| requirements.txt rendered correctly | ✅ |
```