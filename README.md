# mongodb-cheatsheet
Cheat-sheet of mongodb shell commands and more.

## Manually export and restore collection
### Steps
  - mongodump --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"
  - mongoexport --uri="mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies" --collection=sales --out=sales.json
  - mongorestore --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"  --drop dump
  - mongoimport --uri="mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies" --drop sales.json
### Commands
  - mongoimport: can import data from JSON, and other supported non BSON formats.
  - mongodump: exports data in its raw BSON form.
  - mongorestore: imports data from a mongodump created BSON format.
  - mongoexport: does work with JSON, but it would export it, thus making a copy of the data outside of the Atlas cluster, rather than adding a collection to the Atlas cluster.

## Querying collection from Shell
  - db.mycollectionname.query
  - Notes: db is a constant, mycollectionname is the name of the collection. Substitue "query" with the specific query, for example: "db.mycollectionname.find().count()".
  - To display on a readable format with tabulation add method ".pretty()".
  
## Basic commands (alphabetical order)
### show dbs
  List all databases. (Need to be previously connected to a cluster).
### show collections
  List all collections within a database. (Need to be previously connected to a cluster and navigated to a specific database with command "use mydbname").
### use
  Navigate to the specified database as a second parameter. Example: "use mydbname".

## Basic query methods
  ### sort()
  Sort the result of the query

## Comparison operators
### $eq
  EQual to
### $ne
  Not Equal to
### $gt
  Greater Than
### $lt
  Less Than
### $gte
  Greater Than or Equal to
### $lte
  Less Than or Equal to

## Logic operators
### $and
  Match all of the specified query clauses.
### $or
  At least one of the query clauses is matched.
### $nor
  Fail to match both given clauses.
### $not
  Negates the query requirement.
  
## Expressive operator
  Find all documents where the trip started and ended at the same station:
    ```db.trips.find({ "$expr": { "$eq": [ "$end station id", "$start station id"] } })```
