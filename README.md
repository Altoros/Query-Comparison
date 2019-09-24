# Query-Comparison

Repository contains information about setting up databases and import data. 

### Table of content:
  - [Couchbase Setup](#couchbase-setup)
    - [Setting up Couchbase database](#setting-up-couchbase-database)
    - [Import data for Couchbase](#setting-up-couchbase-database)
  - [Mongo Setup](#mongo-setup)
    - [Setting up Mongo database](#setting-up-mongo-database)
    - [Import data for Mongo](#setting-up-mongo-database)
  - [MySQL Setup](#mysql-setup)
    - [Setting up MySQL database](#setting-up-mysql-database)
    - [Import data for MySQL](#setting-up-mysql-database)



## Couchbase setup

### Setting up Couchbase database
Follow the [Install Couchbase process](https://docs.couchbase.com/server/4.0/getting-started/installing.html) for necessary OS.
### Import data for Couchbase
 - Connect to Couchbase Server and create a cluster. Accept all the default settings. 
 - Create a new `crm` bucket.
 - Run commands for importing file from `Couchbase-Data` folder:
   - `./cbimport json -c http://localhost -u Administrator -p <password> -b crm -o ./crm.json -f lines`. For more information: [cbimport](https://docs.couchbase.com/server/current/tools/cbimport.html)
 - Open Couchbase Admin Console and `Sign in`
 - Open Query tab (This will put you in the Query workbench).
 - Copy the content of the `cmrindexes.txt` from `Couchbase-Data` folder into the workbench and run all of them to recreate all the indexes.
## Mongo setup

### Setting up Mongo database
Follow the [Install MongoDB process](https://docs.mongodb.com/manual/installation/) for necessary OS.

### Import data for Mongo
 - Create database `QueryComparasion`
 - Add  to _`path-to-mongodb/bin`_ to `PATH` environment variable
 - Run commands for each file from `MongoDB-Data` folder:
   - `mongoimport --db QueryComparasion --collection account --file account.json`
   - `mongoimport --db QueryComparasion --collection activity --file activity.json`
   - `mongoimport --db QueryComparasion --collection territory --file territory.json`
   - `mongoimport --db QueryComparasion --collection user --file user.json`
 - Check that data is imported correctly

## MySQL setup

### Setting up MySQL database

Download [MySQL Installer](https://dev.mysql.com/downloads/installer/) and
follow the [Install MySQL Guide](https://docs.mongodb.com/manual/installation/) for step-by-step description.
### Import data for MySQL
From MySQL folder:
 - Create database `QueryComparasion`
 - Add  to _`path-to-mysql-server/bin`_ to `PATH` environment variable
 - `mysql -u [user] -p QueryComparasion < data.sql`



