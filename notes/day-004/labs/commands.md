# Commands Used — Day 004

## Navigate to Project

```bash
cd /root/code/fraud-detection
```

---

## Check Project Structure

```bash
tree
```

---

## Rename Incorrect Directories

```bash
mv src/feature src/features
mv src/util src/utils
```

---

## Create Missing Directories

```bash
mkdir -p data/raw
mkdir -p data/processed
mkdir -p tests
mkdir -p configs
```

---

## Create Python Package Files

```bash
touch src/data/__init__.py
touch src/features/__init__.py
touch src/models/__init__.py
touch src/utils/__init__.py
```

---

## Verify requirements.txt

```bash
cat requirements.txt
```

---

## Verify README Heading

```bash
head -n 1 README.md
```