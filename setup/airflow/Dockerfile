FROM apache/airflow:2.10.2
COPY requirements.txt /requirements.txt

COPY ./variables_and_connections /init/variables_and_connections
RUN pip install --no-cache-dir -r /requirements.txt

# install cosmos module
RUN pip install 'astronomer-cosmos[dbt.all]'

# prepare dbt virtual environment
COPY dbt-requirements.txt ./
RUN python -m virtualenv dbt_venv && source dbt_venv/bin/activate && \
    pip install --no-cache-dir -r dbt-requirements.txt && deactivate