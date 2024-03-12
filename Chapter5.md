# Database and web development with Python

## 5.1 Database

### Setup SQLite3 Database

Although Python has modules for many databases, in the following examples we will look at
sqlite3. Although it’s not suited for large, high-traffic applications, sqlite3 has two
advantages:
- Because it’s part of the standard library, it can be used anywhere you need a
database without worrying about adding dependencies.
sqlite3 stores all of its records in a local file, so it doesn’t need both a client and
server, which would be the case for PostgreSQL, MySQL, and other larger databases.
These features make sqlite3 a handy option for both smaller applications and quick
prototypes.

 To use a sqlite3 database, the first thing you need is a Connection object. Getting
a Connection object requires only calling the connect function with the name of
file that will be used to store the data:

```python
import sqlite3
conn = sqlite3.connect("datafile.db")
```

## 5.2 Python Web API with Flask

