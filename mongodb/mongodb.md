mongoDB
======
- a 'document' database
- instead of database rows, MongoDB stores data in flexible, JSON-like documents
- so fields can very from document to document, and data structure can be changed over time
- the *document model* maps to objects in you application code
- MongoDb has APIs for loads of languages, including js

mongoose
--------
- a wrapper for MongoDB js API, making it easier to write validation, type-casting,
  query building, business logic hooks etc


SQL clauses v statements
-------------------------
- a clause is a single atomic piece of syntax - usually part of a statement e.g. `WHERE x = y`
- a statement = the whole SQL command, e.g `SELECT foo FROM bar WHERE x = y;`

Join (SQL)
----------
- a join clause combines columns from one or more tables, in a relational database
- it creates a new set
- a means to combine columns from one (self-table) or more tables by using values
  common to each
- the programmer declares a `JOIN` statement to identify rows for joining. If the
  evaluated predicate is true, the combined ro is produced.
- there are 5 types of join (4 different ways to join tables)
  1. `CROSS JOIN`: cartesian product of rows from tables in the join. It produces
     a set of rows that combines every row from the first table with every row
     from the second table. No predicate is applied to filter rows from the
     resulting table.
  2. `INNER JOIN`: requires each resulting row to have matching column values,
     ie. the join-predicate must be satisfied.
      ```
      SELECT employee.LastName, employee.DepartmentID, department.DepartmentName
      FROM employee
      INNER JOIN department ON
      employee.DepartmentID = department.DepartmentID
      ```
  3. `OUTER JOIN`: retains each row, even if no other matching row exists. 3 types:
    1. `LEFT OUTER JOIN`: a.k.a. left join. Returns matching joined rows, and
        any rows from the first table (left hand side of the join statement) that
        weren't matched, with `null` in each column from the right hand side table.
    2. `RIGHT OUTER JOIN`: returns matching rows, plus all other rows from right
      hand side table, with null values for fields from left hand side table.
    3. `FULL OUTER JOIN`: left outer join + right outer join. Union of the 2 sets,
       with `null` in any missing fields, as before
  4. `SELF JOIN`: joining a table to itself


MongoDB
--------
#### sharding
 - a method for distributing data across multiple machines
 - horizontal scaling - diving the dataset and load over multiple servers

#### `$lookup`
  - performs a left outer join to an unsharded collection in the same database
    to filter in documents from the “joined” collection for processing

mongoose
---------
#### `populate`
- a more powerful alternative to mongoDB's `lookup`
- like a join
- it returns the document (object), with ForeignKeys replaced with the documents they refer to instead
- so it aggregates data (like a join)
- e.g. `Story` has an `author` field, which has a foreign key to a `Person`. Once
  the `populate` has occurred, in the resulting object, the author can be accessed
  in full at `story.author`
```js
Story.
  findOne({ title: 'Casino Royale' }).
  populate('author').
  exec(function (err, story) {
    if (err) return handleError(err);
    console.log('The author is %s', story.author.name);
    // prints "The author is Ian Fleming"
  });
```

##### field selection
- if we only want the populated document returned to include specified fields,
  rather than all fields from the right hand side table in the join, you can
  pass the fields using mongoose's *field name syntax* as the second argument to
  the `populate` method.

##### populating multiple paths
 - just call `populate()` multiple times (chain them)


#### `findByID(id, [projection], [options], [callback])`
 - Finds a single document by its `_id` field. `findById(id)` is almost
equivalent to `findOne({ _id: id })` (except in its handling of `undefined`)
