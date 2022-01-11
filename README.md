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

## Basic commands (alphabetical order)
### show dbs
  List all databases. (Need to be previously connected to a cluster).
### use
  Navigate to the specified database as a second parameter. Example: "use mydbname".
