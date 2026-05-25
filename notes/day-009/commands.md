# Commands Used — Day 009

## Navigate to Template Directory

```bash
cd /root/code/mlops-template
```

---

## View Cookiecutter Configuration

```bash
cat cookiecutter.json
```

---

## Generate ML Project from Template

```bash
cookiecutter /root/code/mlops-template/ -o /root/code/ --no-input project_name=churn-model ml_framework=sklearn
```

---

## Verify Generated Project Structure

```bash
tree /root/code/churn-model
```

---

## Verify Generated Requirements

```bash
cat /root/code/churn-model/requirements.txt
```

---

## Verify Generated README

```bash
cat /root/code/churn-model/README.md
```