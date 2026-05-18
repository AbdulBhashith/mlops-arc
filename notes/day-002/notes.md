# Notes — Day 002

## Important Concepts

### 1. Jupyter Server Binding

- `127.0.0.1` allows only local access
- `0.0.0.0` allows external/proxy access

This is critical in cloud labs and production systems.

---

## 2. Notebook Root Directory

The notebook directory defines where notebooks are stored and accessed from.

Incorrect paths prevent JupyterLab from starting.

---

## 3. Port Configuration

The lab environment expected JupyterLab on:

```text
Port: 8888
```

Using the wrong port breaks proxy routing.

---

## 4. Running Services in Background

Using:

```bash
&
```

runs the server in the background so the shell remains usable.

---

## 5. Virtual Environment Usage

Using a Python virtual environment ensures:

- isolated dependencies
- predictable package versions
- cleaner environments

---

## Troubleshooting Checklist

| Check | Status |
|------|------|
| Virtual environment activated | ✅ |
| Notebook directory exists | ✅ |
| Correct port configured | ✅ |
| Correct IP binding configured | ✅ |
| Jupyter process running | ✅ |