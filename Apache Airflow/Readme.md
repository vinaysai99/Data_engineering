# Apache Airflow Data Engineering Repository

This repository contains my journey and learning experiences with Apache Airflow for data engineering. It includes various data pipelines implemented as Python (.py) files that demonstrate different Airflow concepts and use cases.

## 📋 Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Setup Instructions](#setup-instructions)
- [Important Terminal Commands](#important-terminal-commands)
- [Data Pipeline Examples](#data-pipeline-examples)
- [Lessons Learned](#lessons-learned)
- [Resources](#resources)

## 🔍 Overview

This repository documents my learning journey in data engineering, specifically focused on Apache Airflow. Here, you'll find various data pipeline implementations, configurations, and best practices I've learned along the way.

Apache Airflow is an open-source platform for developing, scheduling, and monitoring batch-oriented workflows. Airflow's dags (directed acyclic graphs) make it easy to visualize pipeline dependencies, progress, logs, code, trigger tasks, and success status.

## 📁 Repository Structure

```
airflow-data-engineering/
├── dags/                  # DAG definitions
└── config/                # Configuration files
```

## 🚀 Setup Instructions

### Prerequisites

- Python 3.8+
- pip
- virtualenv (recommended)

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/vinaysai99/Data_engineering.git
   cd Apache Airflow
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install Apache Airflow and dependencies:
   ```bash
   pip install "apache-airflow==2.7.1" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.7.1/constraints-3.8.txt"
   pip install -r requirements.txt
   ```

4. Initialize the Airflow database:
   ```bash
   airflow db init
   ```

5. Create an admin user:
   ```bash
   airflow users create \
     --role Admin \
     --username admin \
     --email admin \
     --firstname admin \
     --lastname admin \
     --password admin
   ```

6. Start the Airflow webserver and scheduler:
   ```bash
   airflow webserver --port 8080
   airflow scheduler
   ```

7. Access the Airflow UI at `http://localhost:8080`

## 🖥️ Important Terminal Commands

Here are some essential Airflow commands for reference:

```bash
# Initialize the database
airflow db init

# Reset the database (caution: this will delete all data)
airflow db reset

# Create an admin user
airflow users create --role Admin --username admin --email admin --firstname admin --lastname admin --password admin

# Find the process ID of the Airflow scheduler
lsof -i :8793

# Start the Airflow webserver (default port: 8080)
airflow webserver

# Start the Airflow scheduler
airflow scheduler

# List all DAGs
airflow dags list

# Trigger a DAG run
airflow dags trigger [dag_id]

# Pause a DAG
airflow dags pause [dag_id]

# Unpause a DAG
airflow dags unpause [dag_id]

# List tasks in a DAG
airflow tasks list [dag_id]

# Test a specific task
airflow tasks test [dag_id] [task_id] [execution_date]

# Backfill a DAG
airflow dags backfill -s [start_date] -e [end_date] [dag_id]
```

## 📊 Data Pipeline Examples

Below are some examples of the data pipelines included in this repository:

1. **ETL Pipeline**: Extract data from various sources, transform it, and load it into a data warehouse.
2. **Data Validation Pipeline**: Validate data quality and integrity before processing.
3. **Sensor-based Pipeline**: Wait for conditions to be met before proceeding with tasks.
4. **Branching Pipeline**: Execute different paths based on conditions.
5. **Dynamic DAG Generation**: Generate DAGs dynamically based on configuration.

## 📚 Lessons Learned

Throughout my Airflow journey, I've learned several important concepts:

- DAG design patterns and best practices
- Task dependencies and execution flow
- Error handling and retries
- Scheduling strategies
- Performance optimization
- Custom operators and hooks
- Testing and debugging DAGs

## 🔗 Resources

- [Apache Airflow Documentation](https://airflow.apache.org/docs/)
- [Airflow GitHub Repository](https://github.com/apache/airflow)
- [Awesome Apache Airflow](https://github.com/jghoman/awesome-apache-airflow)
- [Airflow Best Practices](https://airflow.apache.org/docs/apache-airflow/stable/best-practices.html)

## 📝 Contributing

Feel free to fork this repository and submit pull requests with improvements or additional examples!

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
