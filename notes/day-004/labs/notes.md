# Notes — Day 004

## Important Concepts

### 1. Standard ML Project Structure

A standardized structure improves:

- readability
- maintainability
- collaboration
- scalability

---

## 2. Python Package Initialization

`__init__.py` files allow Python to treat directories as packages.

Example:

```bash
touch src/utils/__init__.py
```

---

## 3. Data Organization

Separating raw and processed data helps maintain:

- reproducibility
- data lineage
- cleaner workflows

Structure:

```text
data/
├── raw/
└── processed/
```

---

## 4. Dependency Management

`requirements.txt` tracks project dependencies.

Required packages:

- scikit-learn
- pandas
- numpy
- mlflow

---

## 5. Naming Conventions

Consistent folder naming improves project consistency across teams.

Examples:

| Preferred | Avoid |
|-----------|------|
| `features/` | `feature/` |
| `utils/` | `util/` |

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Folder structure correct | ✅ |
| Missing directories created | ✅ |
| `__init__.py` files added | ✅ |
| README heading updated | ✅ |
| requirements.txt updated | ✅ |