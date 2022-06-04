## Things I want to know more about

<h1> SQL vs NoSQL Database:</h1>

* SQL Database Examples:
1. MySQL Community Edition:
 1. Replication.
 2. Sharding.
 3. Memcached as a NoSQL API to MySQL.
 4. Maturity.
 5. Wide range of Platforms and Languages.
 6. Cost effectiveness.
2. MS-SQL Server Express Edition
 1. Integrated Development Environment.
 2. Disaster Recovery.
 3. Cloud back-up.
3. Oracle Express Edition:
 1. Easy to Upgrade.
 2. Wide platform support.
 3. Scalability

* NoSQL Database Examples:
1. MongoDB
 1. Speed.
 2. Scalability.
 3. Manageable.
 4. Dynamic Schema.

2. CouchDB
 1. Schema-lesS.
 2. HTTP query.
 3. Conflict Resolution.
 4. Easy Replication.
3. Redis
 1. Data structures.
 2. Redis as Cache.
 3. Very fast.

 [nosql vs sql](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)</br>
 </br>
 [Sql vs NoSql](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y)</br>
 ===========================================================================================================
<h1>sql modeling techniques</h1>

 * Data Modeling – Table Elements:</br>
 ![Table Elements](https://www.essentialsql.com/wp-content/uploads/2021/11/Database-Table-Data-Modeling.png)

 * Data Modeling – Table Relationships:</br>
 ![Table Relationships](https://www.essentialsql.com/wp-content/uploads/2014/06/DataModel-Relations1.png)

    Cardinality	        Notation
 1. zero or one-to-many	  0..*
 2. one-to-many	          1..*
 3. zero or one-to-one	  0..1
 4. one-to-one	          1..1

 [sql modeling techniques](https://www.essentialsql.com/get-ready-to-learn-sql-7-simplified-data-modeling/)
 ===========================================================================================================

 <h1>Sequelize v6</h1>
 Installing:
 ---
 npm install --save sequelize
 ---

 ---
 const { Sequelize } = require('sequelize');

// Option 1: Passing a connection URI
const sequelize = new Sequelize('sqlite::memory:') // Example for sqlite
const sequelize = new Sequelize('postgres://user:pass@example.com:5432/dbname') // Example for postgres

// Option 2: Passing parameters separately (sqlite)
const sequelize = new Sequelize({
  dialect: 'sqlite',
  storage: 'path/to/database.sqlite'
});

// Option 3: Passing parameters separately (other dialects)
const sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialect: /* one of 'mysql' | 'mariadb' | 'postgres' | 'mssql' */
});
---

* Testing the connection:
---
try {
  await sequelize.authenticate();
  console.log('Connection has been established successfully.');
} catch (error) {
  console.error('Unable to connect to the database:', error);
}
---
* Closing the connection:
- Sequelize will keep the connection open by default, and use the same connection for all queries. If you need to close the connection, call sequelize.close() (which is asynchronous and returns a Promise). 
- Once sequelize.close() has been called, it's impossible to open a new connection. You will need to create a new Sequelize instance to access your database again.

[sequelize api](https://sequelize.org/docs/v6/getting-started/#installing)</br>


