# Project: Sparkify-data-modeling 

## Summary
* [CQL queries] (#CQL)
* [Problem](#Problem)
* [Project structure](#Structure)

--------------------------------------------

#### CQL

* 1. Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4

``` SQL
CREATE TABLE IF NOT EXISTS music_library_session_data
		(sessionId int, itemInSession int,artist_name text, 
		 song_title text, song_length text,
         PRIMARY KEY ((sessionId, itemInSession)))
```

<br>In this case session_id and session_item_number are enough to make a record unique for our request. 
PRIMARY KEY is composed by both session_id and session_item_number.

* 2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
* 3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own

--------------------------------------------

#### Problem

Modeling your NoSQL database or Apache Cassandra database Design tables to answer the queries outlined in the project template.
* Write Apache Cassandra <code>CREATE KEYSPACE</code> and <code>SET KEYSPACE</code> statements
* Develop your <code>CREATE</code> statement for each of the tables to address each question
* Load the data with <code>INSERT</code> statement for each of the tables
* Include <code>IF NOT EXISTS</code> clauses in your <code>CREATE</code> statements to create tables only if the tables do not already exist.
We recommend you also include DROP TABLE statement for each table, this way you can run drop and create tables whenever you want to reset your database and test your ETL pipeline
Test by running the proper select statements with the correct <code>WHERE</code> clause.

--------------------------------------------

#### Structure

* <b> /data </b> - The directory of CSV files partitioned by date.
* <b> /images </b> - an image inside the notebook.
* <b> Project_1B_ Project_Template.ipynb </b> - It is a notebook the solution.
* <b> event_datafile_new.csv - The generated CSV composed by all event_data files.

