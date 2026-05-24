# Notes — Day 008

## Important Concepts

### 1. Pre-Commit Hooks

Pre-commit hooks automatically run checks before Git commits.

Common uses:

- formatting validation
- linting
- YAML validation
- whitespace cleanup

---

## 2. Version Pinning

Every repository entry should include a `rev` field.

Example:

```yaml
rev: v5.0.0
```

This ensures reproducible tooling versions.

---

## 3. Ruff Integration

Ruff provides fast linting and import sorting.

Correct hook configuration:

```yaml
- repo: https://github.com/astral-sh/ruff-pre-commit
  rev: v0.11.13
  hooks:
    - id: ruff
```

---

## 4. Black Integration

Black ensures consistent Python formatting.

Example:

```yaml
- repo: https://github.com/psf/black-pre-commit-mirror
  rev: 25.1.0
  hooks:
    - id: black
```

---

## 5. Common Pre-Commit Hooks

| Hook | Purpose |
|------|----------|
| trailing-whitespace | Removes extra spaces |
| end-of-file-fixer | Ensures newline at file end |
| check-yaml | Validates YAML syntax |
| ruff | Python linting |
| black | Python formatting |

---

## 6. Automatic Version Updates

Command:

```bash
pre-commit autoupdate
```

updates hooks to their latest released versions.

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Hook names corrected | ✅ |
| Ruff repository updated | ✅ |
| All repos include `rev` | ✅ |
| Hooks installed successfully | ✅ |
| `pre-commit run --all-files` passing | ✅ |