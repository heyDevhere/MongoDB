           ** Sab kuch padenge of mongoDB **
(1) basic 
(2) advanced
(3) projects

=> MongoDB Atlas,MongoDB compass bhi padenge

MongoDB company developed "MongoDB atlas" to provide Database service 

**************** Let's Begin ***************************
Introduction to mongoDB

Q) What is mongoDB ?
A) => MongoDB is open source means mongoDB banane ke liye jo bhi code tha voh openly available h

=>it is document oriented NoSQL dataase management system
meaning : it is a database which stores data in it, in the form of documents.
  
=>Designed for handling unstructed data.

=> This Database is developed by a company named as *10gen*
then the company name changed to *MongoDB*

=> this company wanted a large dataase that means this company wanted a *Humangous* Database

* HUMONGOUS *
  remove HU and US now what is left ??
  => MONGO


  Q) Differnce between SQL and MongoDB

              SQL                                                        MongoDB (NoSQL)

  (1) Sql databases are relational databases.                            (1) Nosql databases are non relational databases

  (2) They store structured data                                         (2) Store unstructed semi structired data

  (3) Suitable for application with well-defined schemas                 (3) Ideal for applications with evolving/dynamic databases for example on youtube any body can register
                                                                             at any  time
  
  (4) E-commerce ,HR managment                                           (4) Content managment system,social media platforms,gaming

  (5) SQL is a big term..uske ander Mysql,postgreSQL,oracle              (5) MongoDB,redis
      aata h


                                                       *********      SQL ***************


-- Table: students

| student_id | first_name | last_name | age | grade |
|------------|------------|-----------|-----|-------|
|     1      |   John     |   Doe     |  17 |   11  |
|     2      |   Jane     |  Smith    |  16 |   10  |


-- Table: subjects

| subject_id | subject_name |
|------------|--------------|
|     1      |   Math       |
|     2      |   Science    |


-- Table: grades

| subject_id | student_id | marks |
|------------|------------|-------|
|     1      |     1      |  85   |
|     2      |     1      |  90   |


                                 *******     MongoDB **************
```json
// students collection
[
  {
    "student_id": 1,
    "first_name": "John",
    "last_name": "Doe",
    "age": 17,
    "grade": 11
  },
  {
    "student_id": 2,
    "first_name": "Jane",
    "last_name": "Smith",
    "age": 16,
    "grade": 10
  }
]

// subjects collection
[
  {
    "subject_id": 1,
    "subject_name": "Math"
  },
  {
    "subject_id": 2,
    "subject_name": "Science"
  }
]

// grades collection
[
  {
    "subject_id": 1,
    "student_id": 1,
    "teacher_name":"max",
    "marks": 85
  },
  {
    "subject_id": 2,
    "student_id": 1,
    "marks": 90
  }
]


In grades collection for student_id:1 , i can add an extra field let's say "teacher_name":"max" , without effecting others therefore mondoDB is said to be flexible.

MongoDB is schemaless because ::::

MongoDB mein "schemaless" ka matlab hai ki aapko pehle se define ki gayi rigid schema (jaise traditional SQL databases mein hoti hai) ki zarurat nahi hoti. Iska matlab hai ki aap apne documents mein koi bhi field add ya remove kar sakte hain bina kisi formal schema definition ke. MongoDB flexible schema support karta hai, jisme aap different documents mein different fields ka use kar sakte hain.

Is flexibility ke karan, MongoDB ko "schemaless" database system kaha jata hai. Lekin, yeh flexibility ka matlab yeh nahi hai ki MongoDB mein schema nahi hoti. MongoDB mein bhi schema hoti hai, lekin woh traditional SQL databases ki tarah rigid nahi hoti.

SQL is schema-based !

In mongoDB in one database , there would be multiple collections and in that collections their would be multiple documents , that documents are schemaless


**MongoDB Database
   |
   |-- Collection 1
   |      |
   |      |-- Document 1
   |      |
   |      |-- Document 2
   |      |
   |      |-- Document 3
   |
   |-- Collection 2
   |      |
   |      |-- Document 1
   |      |
   |      |-- Document 2
   |
   |-- Collection 3
          |
          |-- Document 1
          |
          |-- Document 2
**

************************ MongoDB Features **************************************

* Flexible Schema Design

=> schema-less , therefore can accommodate changes in a document

* Document Oriented Storage

=> Data is stored in JSON- like BSON documents ( to be learned )

* Dynamic Queries (indexes) => (to be learned)

* Aggregation framework (to be learned)

* open source

*********************** HOW MONGODB WORKS *******************************

Frontend : HTML,CSS,JS , React js 

Backend : Node js , Express js , Next js 

Node js  requests mongoDB server , to store data in the database.

MongoDB server has a storage engine => WiredTiger

* Storage engine communicates with the database and storage engine main fuction is to read and write data in the database
* Storage engine also converts json data to bson data ( to be learned )

Database : MongoDB

Mongo shell ( playground ) with the help of this , i dont need a backend to talk with database !

*********************     JSON VS BSON ******************************

=> In MongoDB , data is stored internally in BSON format.
   BSON means binery representation of JSON

=> we write data in bson , and the storage engine converts that json into bson. 
                ** WHY **
=> via BSON , there is higher read and write speeds , reduced storage requirements, and improved data manipulation capabilities. 

JSON Data = > Easy to read

{
   "name": "John Doe",
   "age": 30,
   "email": "john.doe@example.com",
   "address": {
      "street": "123 Main St",
      "city": "Anytown",
      "zipcode": "12345"
   },
   "is_active": true,
   "tags": ["mongodb", "database", "nosql"]
}

BSON Data = > Not easy to read (Impossible)

\x1F\x00\x00\x00
\x02\x6E\x61\x6D\x65\x00\x0A\x00\x00\x00\x4A\x6F\x68\x6E\x20\x44\x6F\x65
\x10\x61\x67\x65\x00\x1E\x00\x00\x00
\x02\x65\x6D\x61\x69\x6C\x00\x18\x00\x00\x00\x6A\x6F\x68\x6E\x2E\x64\x6F
\x65\x40\x65\x78\x61\x6D\x70\x6C\x65\x2E\x63\x6F\x6D
\x03\x61\x64\x64\x72\x65\x73\x73\x00
\x30\x00\x00\x00\x03\x73\x74\x72\x65\x65\x74\x00\x1B\x00\x00\x00\x31\x32
\x33\x20\x4D\x61\x69\x6E\x20\x53\x74\x00\x41\x6E\x79\x74\x6F\x77\x6E\x00
\x00
\x00\x01\x69\x73\x5F\x61\x63\x74\x69\x76\x65\x00\x01
\x74\x61\x67\x73\x00\x29\x00\x00\x00\x04\x30\x00\x08\x00\x00\x00\x6D\x6F
\x6E\x67\x6F\x64\x62\x00\x01\x00\x00\x00\x04\x31\x00\x08\x00\x00\x00\x64
\x61\x74\x61\x62\x61\x73\x65\x00\x03\x00\x00\x00\x6E\x6F\x73\x71\x6C\x00


MongoDB installation TimeStamb=> [ 38 to 44 ]

** IN CMD **

Command: mongosh
desc: to enter in the mongo shell

Command: show dbs / show databases
desc: to see the databases already present in mongoDB

admin,config,local are defult databases present in mongoDB

Command: use <database-name>
desc: new database create
and to swtich to a database 

Command:db.dropDatabse()
desc: to delete the database ( it will delete the current database which we were using )

Command: show collections;
desc:to see collections of the current using database

Command: db.createCollection('<collection-name>');
desc:to create a collection

Command:dp.<collection-name>.drop();
desc:to delete a collection

Command:db.collectionname.find()
desc: this command returns all the data present in the collection=>collectionaname

** you wont see a database listed in the output of the "show dbs" command until that database contains at least one collection with data in it.  **

**************************************************** INSERT OPERATIONS IN MONGODB ***********************************************

* It inserts one document

db.collectionName.insertOne({
   field1:value1,
   field2:value2,
})

* It inserts multiple documents

db.collectionName.insertMany(
  [ { document 1},
    { document 2},
    { document 3 } ..
  ]
)

after successfull insertion mongoDB assigns us Inserted Id for each document.



![image](https://github.com/heyDevhere/MongoDB/assets/132212030/0e676d90-7e9a-412e-9314-0b2b0d7217c0)








 















