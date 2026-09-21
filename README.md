# yuvraj-airflow
# Airflow DAG Practical — Terminal Commands

## 1. Create Project

```bash
mkdir DAG
cd DAG
```

If the project already exists:

```bash
cd /workspaces/DAG
```

---

## 2. Create Virtual Environment

```bash
python -m venv DAG
```

Activate it:

```bash
source DAG/bin/activate
```

---

## 3. Check Airflow

```bash
airflow version
```

Expected:

```text
3.3.2
```

---

## 4. Set Airflow Home

```bash
export AIRFLOW_HOME=/workspaces/DAG
```

Check:

```bash
echo $AIRFLOW_HOME
```

Expected:

```text
/workspaces/DAG
```

---

## 5. Initialize Airflow Database

```bash
airflow db migrate
```

---

## 6. Create DAG Folder

```bash
mkdir -p dags
```

---

## 7. Create DAG File

Create:

```text
dags/aiops_workflow.py
```

Put the required DAG code inside this file.

---

## 8. Start Airflow DAG Processor

Open a **new terminal**.

```bash
cd /workspaces/DAG
```

```bash
source DAG/bin/activate
```

```bash
export AIRFLOW_HOME=/workspaces/DAG
```

Start the processor:

```bash
airflow dag-processor
```

### IMPORTANT

Keep this terminal running.

---

## 9. Check the DAG

Open another terminal.

```bash
cd /workspaces/DAG
```

```bash
source DAG/bin/activate
```

```bash
export AIRFLOW_HOME=/workspaces/DAG
```

Check DAGs:

```bash
airflow dags list
```

Find:

```text
aiops_workflow
```

---

## 10. Test the DAG

```bash
airflow dags test aiops_workflow 2026-09-20
```

The important output should contain:

```text
CPU: 87
Memory: 65
Response Time: 420 ms
```

Then:

```text
Metrics processed successfully
```

Then:

```text
Anomaly detected: High CPU usage
```

Finally:

```text
===== AIOps Report =====
Metrics collected successfully
Metrics processed successfully
Anomaly detection completed
========================
```

At the end:

```text
state=success
```

means the DAG executed successfully.

---

# Complete Command List

For quick revision, these are the commands you actually need to remember:

```bash
mkdir DAG
cd DAG

python -m venv DAG
source DAG/bin/activate

airflow version

export AIRFLOW_HOME=/workspaces/DAG

airflow db migrate

mkdir -p dags

airflow dag-processor
```

Then, in a **second terminal**:

```bash
cd /workspaces/DAG
source DAG/bin/activate
export AIRFLOW_HOME=/workspaces/DAG

airflow dags list

airflow dags test aiops_workflow 2026-09-20
```

---

# If You Get "No data found"

Make sure:

```bash
export AIRFLOW_HOME=/workspaces/DAG
```

Then keep the DAG processor running:

```bash
airflow dag-processor
```

Wait a few seconds and run:

```bash
airflow dags list
```

---

# If You Want to Stop Airflow

In the terminal running the DAG processor:

```text
CTRL + C
```

---

# Exam Workflow

```text
1. Create/activate environment
        ↓
2. Set AIRFLOW_HOME
        ↓
3. airflow db migrate
        ↓
4. Create dags/aiops_workflow.py
        ↓
5. airflow dag-processor
        ↓
6. Open second terminal
        ↓
7. airflow dags list
        ↓
8. airflow dags test aiops_workflow 2026-09-20
        ↓
9. Check state=success
```

# Important

You do **not** need to run:

```bash
airflow webserver
```

or:

```bash
airflow scheduler
```

for the practical test we used.

The `airflow dag-processor` + `airflow dags test` workflow is enough for the DAG practical we completed.
