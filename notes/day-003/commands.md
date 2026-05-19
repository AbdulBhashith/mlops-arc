# Commands Used — Day 003

## View Dependency File

```bash
cat requirements.in
```

---

## Generate Lockfile

```bash
uv pip compile requirements.in -o requirements.txt
```

---

## Verify Generated Lockfile

```bash
cat requirements.txt
```