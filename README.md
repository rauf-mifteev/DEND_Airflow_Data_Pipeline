# Data pipeline in Apache Airflow project for Udacity Data Engineer Nanodegree

## Project overview
This is Data pipeline project for Udacity Data Engineer Nanodegree. In this project I create 
an **Apache Airflow DAG** (Directed acyclic graph) for automation and monitoring to the **ETL** processe. **ETL pipeline** itself extracts data from **AWS S3**, transforms it using **Amazon Redshift** for staging. This JSON files represent a user activity logs collected by a music streaming app of an imaginary startup Sparkify. And the resulting database will be used for analytical purposes.

## Files in this project
* `create_tables.py`: Drops previous schema and creates empty tables
* `sql_queries.py`: Defines queries used in the ETL pipeline
* `udac_example_dag.py`: Sets up the DAG, assigns operators to each task in the Airflow pipeline and defines the sequence of tasks
* `stage_redshift.py`: Defines StageToRedshiftOperator that reads from S3 and writes to staging tables in AWS Redshfit
* `load_fact.py`: Defines LoadFactOperator that extracts data from staging into `songplays` fact table
* `load_dimension.py`: Defines LoadDimensionOperator that extracts data from staging into the `songs`, `users`, `artists`, and `time` dimension tables
* `data_quality.py`: Defines DataQualityOperator that runs a data quality check to ensure data has been written to RedShift
  
## Datasets

* Song data: `s3://udacity-dend/song_data`
* Log data: `s3://udacity-dend/log_data`

## Database schema

### Fact Table:
* songplays: Records of song plays in log files 

### Dimension Tables:
* artists: Artists in the music database
* songs: Songs in the music database
* users: Users of the app
* time: Timestamps of records

## Prerequisites
The code is **Python** script and it requires:

* [AWS Account with S3 access](https://aws.amazon.com/)
* [AWS Redshift cluster](https://aws.amazon.com/redshift)
* [Apache Airflow](https://https://airflow.apache.org/start.html/)

