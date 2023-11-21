Orchestrate OpenSearch operations with Apache Airflow
===================================================

This repository contains the DAG code used in the [Orchestrate OpenSearch operations with Apache Airflow tutorial](https://docs.astronomer.io/learn/airflow-opensearch). 

The DAG in this repository uses the following package:

- [OpenSearch Airflow provider](https://airflow.apache.org/docs/apache-airflow-providers-opensearch/stable/index.html). 
- [Pandas](https://pandas.pydata.org/)

# How to use this repository

This section explains how to run this repository with Airflow. Note that you will need to copy the contents of the `.env_example` file to a newly created `.env` file. By default the connection shown will connect to the local OpenSearch instance created in the `docker-compose.override.yml` file, if you want to connect to your own remote instance you will need to adjust the values in the `AIRFLOW_CONN_OPENSEARCH_DEFAULT` json. 
No additional tools or packages other than the Astro CLI need to be installed locally to run this repo.

Download the [Astro CLI](https://docs.astronomer.io/astro/cli/install-cli) to run Airflow locally in Docker. `astro` is the only package you will need to install locally.

1. Run `git clone https://github.com/astronomer/airflow-opensearch-tutorial.git` on your computer to create a local clone of this repository.
2. Install the Astro CLI by following the steps in the [Astro CLI documentation](https://docs.astronomer.io/astro/cli/install-cli). Docker Desktop/Docker Engine is a prerequisite, but you don't need in-depth Docker knowledge to run Airflow with the Astro CLI.
3. Run `astro dev start` in your cloned repository.
4. After your Astro project has started. View the Airflow UI at `localhost:8080`.

In this project `astro dev start` spins up 5 Docker containers:

- The Airflow webserver, which runs the Airflow UI and can be accessed at `https://localhost:8080/`.
- The Airflow scheduler, which is responsible for monitoring and triggering tasks.
- The Airflow triggerer, which is an Airflow component used to run deferrable operators.
- The Airflow metadata database, which is a Postgres database that runs on port 5432.
- A local OpenSearch instance, which runs on port 9200.

## Data 

The example DAG in this repository performs document ingest and search on the lyrics from the musical [Hamilton](https://hamiltonmusical.com/new-york/). The data is stored in the `include` folder and was retrieved form this [Kaggle dataset](https://www.kaggle.com/datasets/lbalter/hamilton-lyrics).

## Resources

- [Orchestrate OpenSearch operations with Apache Airflow](https://docs.astronomer.io/learn/airflow-opensearch).
- [OpenSearch Airflow provider documentation](https://airflow.apache.org/docs/apache-airflow-providers-opensearch/stable/index.html).
- [OpenSearch documentation](https://opensearch.org/docs/latest/).


