# Commands Used — Day 002

## Activate Virtual Environment

```bash
source /root/code/ml-env/bin/activate
```

---

## Create Notebook Directory

```bash
mkdir -p /root/notebooks
```

---

## Start JupyterLab Server

```bash
jupyter lab --config=/root/code/jupyter_lab_config.py --allow-root --no-browser &
```

---

## Verify Jupyter Process

```bash
ps -ef | grep jupyter
```

---

## Verify Listening Port

```bash
ss -tulnp | grep 8888
```