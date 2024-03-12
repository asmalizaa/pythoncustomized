# Database and web development with Python

## 5.1 Database

### Setup SQLite3 Database

Although Python has modules for many databases, in the following examples we will look at
sqlite3. Although it’s not suited for large, high-traffic applications, sqlite3 has two
advantages:
- Because it’s part of the standard library, it can be used anywhere you need a
database without worrying about adding dependencies.
sqlite3 stores all of its records in a local file, so it doesn’t need both a client and
server, which would be the case for PostgreSQL, MySQL, and other larger databases.
These features make sqlite3 a handy option for both smaller applications and quick
prototypes.

 To use a sqlite3 database, the first thing you need is a Connection object. Getting a Connection object requires only calling the connect function with the name of file that will be used to store the data:

```python
import sqlite3
conn = sqlite3.connect("datafile.db")
```

The second step is creating a Cursor object from the connection:

```python
cursor = conn.cursor()
print(cursor)
```

### Apply CRUD Operations on SQLite3

At this point, you’re able to make queries against the database. In the current situation, because the database has no tables or records yet, you first need to create a table and insert a couple of records:

```python
cursor.execute("insert into people (name, count) values ('Bob', 1)")
cursor.execute("insert into people (name, count) values (?, ?)", ("Jill", 15))
cursor.execute("insert into people (name, count) values (:username, :usercount)", {"username": "Joe", "usercount": 10})
conn.commit()
```

The last insert query illustrates the preferred way to make a query with variables. Rather than constructing the query string, it’s more secure to use a ? for each variable and then pass the variables as a tuple parameter to the execute method. The advantage is that you don’t need to worry about incorrectly escaping a value; sqlite3 takes care of it for you.

After a table is populated, you can query the data by using SQL commands, again using either ? for variable binding or names and dictionaries:

```python
result = cursor.execute("select * from people")
print(result.fetchall())
result = cursor.execute("select * from people where name like :name", {"name": "bob"})
print(result.fetchall())
```

We can also execute statement to update the record.

```python
cursor.execute("update people set count=? where name=?", (20, "Jill"))
result = cursor.execute("select * from people")
print(result.fetchall())
```

In addition to the fetchall method, the fetchone method gets one row of the result, and fetchmany returns an arbitrary number of rows. For convenience, it’s also possible to iterate over a cursor object’s rows similarly to iterating over a file: 

```python
result = cursor.execute("select * from people")
for row in result:
    print(row)
```

Finally, by default, sqlite3 doesn’t immediately commit transactions. This fact means that you have the option of rolling back a transaction if it fails, but it also means that you need to use the Connection object’s commit method to ensure that any changes
made have been saved. Doing so before you close a connection to a database is a particularly good idea because the close method doesn’t automatically commit any active transactions:

```python
cursor.execute("update people set count=? where name=?", (20, "Jill"))
conn.commit()
conn.close()
```

## 5.2 ORM and SQLAlchemy

**Object-Relational Mapping**

Object Relational Mapping (ORM) is a technique used in creating a "bridge" between object-oriented programs and, in most cases, relational databases.

When interacting with a database using OOP languages, you'll have to perform different operations like creating, reading, updating, and deleting (CRUD) data from a database. By design, you use SQL for performing these operations in relational databases.

While using SQL for this purpose isn't necessarily a bad idea, the ORM and ORM tools help simplify the interaction between relational databases and different OOP languages.

**SQLAlchemy**

SQLAlchemy is the Python SQL toolkit and Object Relational Mapper that gives application developers the full power and flexibility of SQL.

It provides a full suite of well known enterprise-level persistence patterns, designed for efficient and high-performing database access, adapted into a simple and Pythonic domain language.

SQLAlchemy’s goal is to automate redundant database tasks and provide Python object-based interfaces to the data while still allowing the developer control of the database and access to the underlying SQL.

You can install SQLAlchemy in your environment with pip:

 ```python
pip install sqlalchemy
```

Use SQLAlchemy to replicate what you did in section 5.1: Create a table, add
three rows, query the table, and update one row.

First, you need to import the components you need to connect to the database and
map a table to Python objects.

```python
from sqlalchemy import create_engine, select, MetaData, Table, Column, Integer, String
from sqlalchemy.orm import sessionmaker
```

Now you can think about connecting to the database:

```python
dbPath = 'datafile2.db'
engine = create_engine('sqlite:///%s' % dbPath)
metadata = MetaData(engine)
people = Table('people', metadata, 
        Column('id', Integer, primary_key=True),
        Column('name', String),
        Column('count', Integer),
    )
Session = sessionmaker(bind=engine)
session = Session()
metadata.create_all(engine)
```

 When the table is created, the next step is inserting some records. 

```python
people_ins = people.insert().values(name='Bob', count=1)
str(people_ins)
session.execute(people_ins)
session.commit()
```

 Add another 2 records to the table.

 ```python
session.execute(people_ins, [
            {'name': 'Jill', 'count':15},
            {'name': 'Joe', 'count':10}
            ])
session.commit()
```

Execute another statement to retrieve all records.

```python
result = session.execute(select([people]))
for row in result:
    print(row)
```

You can streamline things a bit and perform multiple inserts by passing in a list of dictionaries of the field names and values for each insert:

```python
result = session.execute(select([people]).where(people.c.name == 'Jill'))
for row in result:
    print(row)
```

You can also use the select() method with a where() method to find a particular
record. In the example, you’re looking for any records in which the name column
equals 'Jill'. Note that the where expression uses people.c.name, with the c
indicating that name is a column in the people table:

```python
result = session.execute(people.update().values(count=20).where(people.c.name == 'Jill'))
session.commit()
result = session.execute(select([people]).where(people.c.name == 'Jill'))
for row in result:
    print(row)
```

## 5.3 Python Web API with Flask

