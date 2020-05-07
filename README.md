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

<br>In this case sessionId and itemInSession are enough to make a record unique for our request. 
<b>PRIMARY KEY</b> is composed by both sessionId and itemInSession.

* 2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182

``` SQL
CREATE TABLE IF NOT EXISTS music_library_session_dataTwo
		(userId int, sessionId int, itemInSession int,artist_name text, 
		 song_title text, song_length text,
         first_name text, last_name text,
    PRIMARY KEY ((userId,sessionId), itemInSession))

```

<br>In this case userId and sessionId are enough to make a record unique for our request but for this request 
we have to order by itemInSession, so we have to declare itemInSession as a <b>CLUSTERING KEY</b>.
Our complete <b>PRIMARY KEY</b> is composed by userId, sessionId, itemInSession

* 3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

``` SQL
CREATE TABLE IF NOT EXISTS music_library_session_dataThree
			(userId int, song_title text,
             first_name text, last_name text,
        PRIMARY KEY ((song_title), userId))"

```
<br>In this case song_title is the <b>PARTITION KEY</b> becuase we have to return all usernames based on the song name. userId is the <b>CLUSTERING KEY</b>, 
becuase more users can listen to the same song, so we need to have a unique record.
Our complete <b>PRIMARY KEY</b> is composed by song_title, userId

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

