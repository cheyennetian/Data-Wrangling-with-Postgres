# Purpose

Sparkify isa company that streams music on a data app. They need a way to gather and analyze their data that is housed in JSON logs of user activity and metadata on the songs in their app. They need a simple way to gather all of this data together into easy to use and query tables so they can perform queries and data analytics on their data. 

# How to use

First, run the create_tables.py to get the tables created and to drop any pre-existing data on those tables. Then, run etl.py to load the data from the directories into the tables.

# Files in the Repository

data: houses the directories holding Sparkify's data
etl.ipynb: jupyter notebook showing the ETL process
test.ipnyb: runs tests to ensure everything is working properly to load the data
create_tables.ipnyb: first drops tables that have been created and then creates tables 
etl.py: contains the ETL process for loading the data using python
sql_queries: contains the code for creating the tables and dropping them

# Database Schema design and ETL Pipeline

#### Schema design
This schema design is a star schema. The songplays table resides at the center of the "star" and holds user activity data that will connect to the users, artists, songs, and time tables. The data is organized into this schema because it is the most straightforward way to gather data about user activity with the least amount of repeated data. Keeping the songplays table in the center, while having more specific data about users, artists, songs, and time as the branches out from the star, makes it so that it is easy to query the songplays table without having to perform many joins on the other tables. 

#### ETL Pipeline
The pipeline for loading the data into this schema works by taking the JSON data collected by Sparkify and loading it into tables. The artists, songs, time, and users table all have data that comes together in the songplays table to create a series of tables that are easy to manage and query while holding all relevant data from Sparkify.