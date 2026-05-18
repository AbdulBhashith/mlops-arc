# Lab 01 — Configure JupyterLab Server

## Objective

Troubleshoot and fix a broken JupyterLab configuration so the notebook server can start correctly and become accessible through the lab interface.

---

## Task Summary

The JupyterLab server had multiple incorrect configuration values:

- Wrong notebook directory
- Incorrect port
- Invalid IP binding
- Missing notebooks directory

The goal was to inspect the configuration file, fix all incorrect settings, create required directories, and start the JupyterLab server successfully.

---

## Environment Details

| Component | Path |
|-----------|------|
| Virtual Environment | `/root/code/ml-env/` |
| Config File | `/root/code/jupyter_lab_config.py` |
| Notebook Directory | `/root/notebooks/` |

---

## Step 1 — Activate Virtual Environment

```bash
source /root/code/ml-env/bin/activate
```

### Purpose

Activates the Python virtual environment where JupyterLab is installed.

---

## Step 2 — Inspect Existing Configuration

### Existing Incorrect Configuration

```python
c.ServerApp.notebook_dir = '/root/wrong-path'
c.ServerApp.port = 8000
c.ServerApp.ip = '1.1.1.1'
```

### Problems Identified

| Setting | Issue |
|---------|------|
| `notebook_dir` | Invalid notebook path |
| `port` | Must use port 8888 |
| `ip` | Must bind to 0.0.0.0 |

---

## Step 3 — Correct the Configuration

### Updated Configuration

```python
# Jupyter configuration file for the xFusionCorp Industries data science team

c.ServerApp.token = ''
c.ServerApp.password = ''
c.ServerApp.disable_check_xsrf = True
c.ServerApp.notebook_dir = '/root/notebooks'
c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
```

---

## Step 4 — Create Missing Notebook Directory

```bash
mkdir -p /root/notebooks
```

### Purpose

Creates the required notebook root directory if it does not already exist.

---

## Step 5 — Start JupyterLab

```bash
jupyter lab --config=/root/code/jupyter_lab_config.py --allow-root --no-browser &
```

### Command Breakdown

| Option | Description |
|--------|-------------|
| `--config` | Uses the custom configuration file |
| `--allow-root` | Allows running Jupyter as root |
| `--no-browser` | Prevents opening a browser |
| `&` | Runs the process in the background |

---

## Verification

Verify the server is running successfully:

```bash
ps -ef | grep jupyter
```

Optional verification:

```bash
ss -tulnp | grep 8888
```

---

## Errors & Fixes

### Error 1 — Notebook Directory Missing

#### Error

```text
No such directory: /root/notebooks
```

#### Fix

```bash
mkdir -p /root/notebooks
```

---

### Error 2 — Jupyter UI Not Opening

#### Cause

The server was:

- Running on the wrong port
- Bound to the wrong IP address

#### Fix

```python
c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
```

---

## Key Learnings

- JupyterLab must bind to `0.0.0.0` for external accessibility
- Incorrect notebook paths prevent server startup
- Port configuration is important for proxy-based environments
- Background execution using `&` keeps the terminal free
- Virtual environments isolate Python dependencies properly

---

## Real-World Relevance

This type of troubleshooting is common in:

- MLOps platforms
- Shared data science environments
- Kubernetes notebook deployments
- Cloud-hosted ML workspaces