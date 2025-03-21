airflow db init
airflow db reset
airflow users  create --role Admin --username admin --email admin --firstname admin --lastname admin --password admin

find pid of airflow scheduler
lsof -i :8793

airflow webserver
airflow scheduler
