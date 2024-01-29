# mongodb-and-mongodb-atlas

A Learning project on How to implement mongodb and leverage the use of mongodb atlas

What is mongodb?
MongoDB is a document database. It stores data in a type of JSON format called BSON.
A record in MongoDB is a document, which is a data structure composed of key value pairs similar to the structure of JSON objects.
For example:
{
title: "Post Title 1",
body: "Body of post.",
category: "News",
likes: 1,
tags: ["news", "events"],
date: Date()
}

SQL vs NoSQL or Document database?
SQL databases are considered relational databases. They store related data in seprate tables. When needed, it is quered from multiple tables to join the data back together.
Whereas, MongoDB is a document database, often refered to as a non-relational database. MongoDB stores data in flexible documents. Instead of having multiple tables you can simply Keep all your related data together. This makes reading your data very fast.
You can still have multiple groups of data too. In MongoDB, instead of tables these are called collections.

Cluster: In other words, Its a group of databases.

mongosh commands:
=> db: To get the current database Name.
=> show dbs: To get all the database names
=> use [databaseName]: To create a new database with specified name.
=> db.createCollection([collectionName]): To create a new collection with specified collection name.
=> db.[collectionName].insertOne([any valid javascript object]) or insertMany: To create one or more document(s) in specified collection.

=> db.[collectionName].find or findOne
-> find(): This method accepts a query object. If left empty, all documents will be returned.
-> findOne(): This method accepts a query object. If left empty, it will return the first document it finds.
PROJECTION: Both find methods accept a second parameter called projection. This parameter is an object that describes which fields to include in the results.

=> db.[collectionName].updateOne or updateMany
OPERATORS: $set, $inc

=> db.[collectionName].deleteOne or deleteMany

QUERY OPERATORS:
=> $eq
=> $ne
=> $gt
=> $gte
=> $lt
=> $lte
=> $in
=> $and
=> $or
=> $nor
=> $not
=> $regex
=> $text
=> $where

UPDATE OPERATORS:

Fields operators:
=> $currentDate
=> $inc
=> $set
=> $rename
=> $unset

Array operators:
=> $addToSet
=> $push
=> $pull
=> $pop

AGGREGATIONS:
=> $out
=> $lookup
=> $count
=> $addFields, $avg
=> $match
=> $project
=> $limit
=> $group

SCHEMA VALIDATION: $jsonSchema
example:
db.createCollection("posts", {
validator: {
$jsonSchema: {
bsonType: "object",
required: [ "title", "body" ],
properties: {
title: {
bsonType: "string",
description: "Title of post - Required."
},
body: {
bsonType: "string",
description: "Body of post - Required."
},
category: {
bsonType: "string",
description: "Category of post - Optional."
},
likes: {
bsonType: "int",
description: "Post like count. Must be an integer - Optional."
},
tags: {
bsonType: ["string"],
description: "Must be an array of strings - Optional."
},
date: {
bsonType: "date",
description: "Must be a date - Optional."
}
}
}
}
})
