Summary:
Startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

In order to analyze their data, a Relational Database Schema for AWS Redshift was created, which can be filled with an ETL pipeline.


Project Details:
For this project, the data will be moved from a public S3 buckets to Amazon Web Services.

S3 Buckets (Data Storage):
Bucket 1 contains info about songs and artists

SONG_DATA='s3://udacity-dend/song_data' 
LOG_DATA='s3://udacity-dend/log_data' 

AWS:

Data is from S3 buckets and loading into Redshift, which is a Data Warehouse with columnar storage. Moving the data to this cloud service will help retrieve data faster and also to store large amounts of data in it.

 we are using STAR schema. This schema consists of one fact table referencing any number of dimension tables, which helps the Sparkify for solving simplified common business logic.

Fact Table: songplays: attributes referencing to the dimension tables
Dimension Tables: users, songs, artists and time table


Project Structure:
create_tables.py - Script will drop old tables (if exist) ad re-create new tables
etl.py - Script will executes the queries that extract JSON data from the S3 bucket and ingest them to Redshift
sql_queries.py - File that contains variables with SQL statement in String formats, partitioned by CREATE, DROP, COPY and INSERT statements
dhw.cfg - Configuration file used that contains info about Redshift, IAM and S3