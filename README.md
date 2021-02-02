# DataWarehouses
### Introduction

In this project, I build an ETL pipekline to help one music streaming startup, Sparkify, to extract their data from **AWS S3** (data storage), stage them in **AWS Redshift** and transform data into a set of dimensional tables so that their analytic team can analyze what songs users are listening to.

### Requirements
This project requires following:
1. AWS account with access to create IAM role and configure AWS Redshift
2. Datasets: two public S3 buckets. One bucket contains info about songs and artists, the second bucket has info about users.

### Installation and Set up
For the database schema
#### Staging Table 
+ **staging_songs** - to store songs and artists
+ **staging_events** - to store actions done by users

#### Fact Table 
+ **songplays** - records in event data associated with song plays i.e. records with page **NextSong**

#### Dimension Tables
+ **users** - users in the app
+ **songs** - songs in music database
+ **artists** - artists in music database
+ **time** - timestamps of records in **songplays** broken down into specific units


#### Data Warehouse Configurations
* Created  IAM user in  AWS account
* Assigned Administrator Access then Attach policies
* Used access  and secret keys to create clients for EC2, S3, IAM, and Redshift.
* Created IAM Role with access to Redshift and S3 bucket (ReadOnly)
* Created RedShift Cluster.

#### ETL Pipeline
+ Created tables to store the data from S3 buckets, the create_tables.py script drop old tables (if exist) then create new tables.
+ Loaded the data from S3 buckets to staging tables in the Redshift Cluster, executing the etl.py script extract JSON data from the S3 bucket into redshift
+ Inserted data into fact and dimension tables from the staging tables by executing sql_queries.py query.

### How to Run

Follow steps below to run the ETL process:

1. Create your fact and dimensions tables by executing the create_tables.py script

2. Execute etl.py script to run the analytic queries on the Redshift database.
