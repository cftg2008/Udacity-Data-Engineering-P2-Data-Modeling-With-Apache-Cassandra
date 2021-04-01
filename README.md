# Project 2: Data Modeling with Apache Cassandra <h1>
### Introduction <h3>
A startup called Sparkify wants to analyze the data they have been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The analytics team wanted a data enginner like you to create a Apache Cassandra database which can create queries on song play data to answer the questions the team has. Your task is to create a database for this analysis. Next is to test your database by running queries given to you by the Sparkify's analytics team and compare the testing results with expected values.

## 1. Databset <h2>
Use one source dataset called "event_data" to create the Apache Cassandra database. The directory of CSV files partitioned by date. Below are examples of filepaths to two files in the dataset:
* event_data/2018-11-08-events.csv
* event_data/2018-11-09-events.csv

### 1.1 Apache Cassandra Queries <h3>
It is important to point out that with Apache Cassandra, you model the database tables on the queries you want to run. That is to say, it is a query-driven design approach. Design queries to answer the following questions:
* Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4
* Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182¶
* Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'
  
### 1.2 Dimension tables <h3>
* users - keeps unique user details with the following columns: user_id (PK), first_name, last_name, gender, level.
* songs - records unique song details with the following columns: song_id (PK), title, artist_id, year, duration.
* artists - stores unique artist details with the following columns: artist_id (PK), name, location, latitude, longitude.
* time - maintains unique time details with the following columns: start_time (PK), hour, day, week, month, year, weekday.

## 2. Files in the project workspace <h2>
In addition to the data/song_data and data/log_data files, the project workspace has the following components:

### 2.1 create_tables.py <h3>
This script does the following:

* Drops (if exists) and creates the sparkify database
* Establishes connection with the sparkify database and gets the database cursor
* Calls the script "drop_table_queries" to drop all the sparkify's tables 
* Calls the script "create_table_queries" to create all the sparkify's tables
* Closes the database connection

### 2.2 sql_queries.py <h3>
This script does the following:

* Drops all the tables with the script "drop_tables_queries"
* Creates all the tables with the script "create_tables_queries"
* Inserts records into various tables when called by the ETL pipeline

### 2.3 etl.ipynb <h3>
This jupyter notedbook contains detailed instructions on the ETL process of each of the tables.

### 2.4 test.ipynb <h3>
This jupyter notedbook contains instructions to check the database construction process. 

### 2.5 etl.py <h3>
This script does the following:

* Reads, processes and loads data from the song_data and log_data files into the tables created in the previous steps

## 3. User guide <h2>
To populate the tables with the data from the entire dataset of the two sources, run the following scripts in the command line window:

* Enter "python3 create_tables.py", follow by the return key
* Enter "python3 etl.py", follow by the return key

After the above steps had completed, one can execute the steps in the test.ipynb scripts to perform data quality checks. 
