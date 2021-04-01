# Project 2: Data Modeling with Apache Cassandra <h1>
### Introduction <h3>
A startup called Sparkify wants to analyze the data they have been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The analytics team wanted a data enginner like you to create a Apache Cassandra database which can create queries on song play data to answer the questions the team has. Your task is to create a database for this analysis. Next is to test your database by running queries given to you by the Sparkify's analytics team and compare the testing results with expected values.

## 1. Databset <h2>
Use one source dataset called "event_data" to create the Apache Cassandra database. The directory of CSV files partitioned by date. Below are examples of filepaths to two files in the dataset:
* event_data/2018-11-08-events.csv
* event_data/2018-11-09-events.csv

Each file is made up of these columns:
- artist
- firstName of user
- gender of user
- item number in session
- last name of user
- length of the song
- level (paid or free song)
- location of the user
- sessionId
- song title
- userId

### 1.1 Apache Cassandra Queries <h3>
It is important to point out that with Apache Cassandra, you model the database tables on the queries you want to run. That is to say, it is a query-driven design approach. So, design queries to answer the following questions:
1. Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4
2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'
  
### 1.2 Query 1 <h3>
The table with the following columns has been created and loaded for Query 1 to work:
* sessionid, itemInSession, artist, song, length 
* PRIMARY KEY(sessionid, itemInSession) - the combination of sessionid and itemInSession will make a unique key
* use SELECT WHERE statement with the conditions sessionId equal to 338 and itemInSession equal to 4 to retrieve the resulting records

### 1.3 Query 2 <h3>
Below table with these columns has been created and loaded for Query 2 to work:
* userid, sessionid, itemInSession, artist, song, firstname, lastname 
* PRIMARY KEY((userid, sessionid), itemInSession)) - the combination of userid, sessionid, and itemInSession will make the primary key unique
* use SELECT WHERE statement with the conditions userid equal to 10 and sessionid equal to 182 plus sorted itemInSession to query the data table

### 1.4 Query 3 <h3>
The table with below columns has been created and loaded for Query 3 to work:
* song, userId, firstname, lastname
* PRIMARY KEY(song, userId) - the combination of song title and userId will make a unique key
* use SELECT WHERE statement with the condition song title equal to 'All Hands Against His Own' to get the resulting rows

## 2. Files in the Project Space <h2>

### 2.1 Project_1B_Template.ipynb <h3>
This jupyter notebook contains detailed instructions on the ETL process to create, load, and query the Apache Cassandra tables to solve the Sparkify analytics team's questions.

### 2.2 Event_datafile_new.csv <h3>
This csv file is subset of the event_datafile_full dataset created for the purpose to insert data into the Apache Cassandra tables
