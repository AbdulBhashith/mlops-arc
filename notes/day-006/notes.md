# Notes — Day 006

## Important Concepts

### 1. Ruff

Ruff is a fast Python linter used for:

- code quality checks
- unused import detection
- import sorting
- style validation

---

## 2. Black

Black is an opinionated Python code formatter.

It automatically formats code into a consistent style.

---

## 3. Shared Line Length Configuration

Both Ruff and Black should use the same line length value.

Example:

```toml
line-length = 120
```

This avoids formatting conflicts.

---

## 4. Ruff Configuration Schema

Modern Ruff versions require lint rules under:

```toml
[tool.ruff.lint]
```

Example:

```toml
[tool.ruff.lint]
select = ["E", "F", "W", "I"]
```

---

## 5. Common Ruff Rules

| Rule | Purpose |
|------|----------|
| E | pycodestyle errors |
| F | Pyflakes checks |
| W | pycodestyle warnings |
| I | Import sorting |

---

## 6. Automated Fixing

Command:

```bash
ruff check src/ --fix
```

can automatically resolve many linting issues.

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Ruff line length set to 120 | ✅ |
| Black line length set to 120 | ✅ |
| Ruff lint schema corrected | ✅ |
| Required lint rules added | ✅ |
| Source formatting fixed | ✅ |
| Ruff checks passing | ✅ |
| Black checks passing | ✅ |