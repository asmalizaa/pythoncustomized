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

Next is to create a table.

```python
# create table
cursor.execute("create table people (id integer primary key, name text, count integer)")
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
from sqlalchemy import create_engine, Column, Integer, String, ForeignKey
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker, relationship
```

Now you can think about connecting to the database:

```python
# Create an SQLite database
engine = create_engine("sqlite:///mydatabase.db", echo=True)

Base = declarative_base()

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True)
    username = Column(String, unique=True)
    posts = relationship("Post", backref="author")

class Post(Base):
    __tablename__ = "posts"
    id = Column(Integer, primary_key=True)
    title = Column(String)
    content = Column(String)
    user_id = Column(Integer, ForeignKey("users.id"))

Base.metadata.create_all(engine)
```

Before we start working with the database, we need to create session first.

```python
# Create a session
Session = sessionmaker(bind=engine)
session = Session()
```

 When the table is created, the next step is inserting some records. 

```python
# Add first data
user1 = User(username="alice")
post1 = Post(title="Hello, World!", content="My first post", author=user1)
session.add(user1)
session.add(post1)
session.commit()
```

 Add another records to the table.

 ```python
# Add second data
user2 = User(username="john")
post2 = Post(title="Test Post", content="This is a test", author=user2)
session.add(user2)
session.add(post2)
session.commit()
```

```python
# Add third data
user3 = User(username="bob")
post3 = Post(title="Test Post2", content="This is a test2", author=user3)
session.add(user3)
session.add(post3)
session.commit()
```

Execute another statement to retrieve all records.

```python
result = session.query(User).all()
for row in result:
    print("ID: {}".format(row.id))
    print("Username: {}".format(row.username))
    for post in row.posts:
        print("ID Post: {}".format(post.id))
        print("Title: {}".format(post.title))
        print("Content: {}".format(post.content))
```

You can also use the select() method with a filter_by() method to find a particular record. In the example, you’re looking for any records in which the username column equals 'alice'.

```python
# Query data with filter
result = session.query(User).filter_by(username="alice").first()
print(f"User: {result.username}, Post: {result.posts[0].title}")
```

To delete record.

```python
# delete record from table
user = session.query(User).get(1)
session.delete(user)
session.commit()
```

Update record.

```python
# update user record
session.query(User).\
    filter(User.username == "john").\
    update({'username': "John Smith"})
session.commit()
```

```python
# update post record
session.query(Post).\
    filter(Post.id == 2).\
    update({'title': "Python Programming", 
            "content" : "Python Programming for PCEP"})
session.commit()
```

## 5.3 Python Web API with Flask

REST stands for REpresentational State Transfer and is an architectural style used in modern web development. It defines a set or rules/constraints for a web application to send and receive data. In this topic, we will build a REST API in Python using the Flask framework. 

Flask is a lightweight Python web framework that allows you to create web applications and build RESTful APIs with ease. Let’s dive into creating a simple REST API using Flask:

Reference: (https://www.askpython.com/python-modules/flask/flask-crud-application)

1. Setting Up Your Flask Project:
   - First, create a virtual environment for your project.
   - Install Flask using pip install flask.

     ```python
     pip install flask_sqlalchemy
     ```

2. Creating Your First REST API Endpoint:
   - Define a Flask app and create an endpoint that returns data in JSON format.
   - Here’s a basic example:

     ```python
     from flask import Blueprint, Flask,render_template,request,redirect
     from models import db,EmployeeModel

     app = Flask(__name__)
     app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///testdb.db'
     app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

     simple_page = Blueprint('simple_page', __name__,
                        template_folder='templates')
     app.register_blueprint(simple_page)

     db.init_app(app)

     @app.before_request
     def create_table():
     	db.create_all()
     ```

3. Handling Different HTTP Request Methods:
   - Let's create a method that will launch the html form to add new record.

     ```python
     @app.route('/data/create' , methods = ['GET','POST'])
     def create():
     	if request.method == 'GET':
     		return render_template('createpage.html')

     	if request.method == 'POST':
     		employee_id = request.form['employee_id']
     		name = request.form['name']
     		age = request.form['age']
     		position = request.form['position']
     		employee = EmployeeModel(employee_id=employee_id, name=name, age=age, position = position)
     		db.session.add(employee)
     		db.session.commit()
     		return redirect('/data')
	```
 
 - Once the record was successfully created, the request will be redirected to another function that will render the datalist.html

   ```python
   @app.route('/data')
   def RetrieveDataList():
   	employees = EmployeeModel.query.all()
   	return render_template('datalist.html',employees = employees)
   ```
 
 - Next function will process a request for a single record.

   ```python
   @app.route('/data/<int:id>')
   def RetrieveSingleEmployee(id):
   	employee = EmployeeModel.query.filter_by(employee_id=id).first()
   	if employee:
   		return render_template('data.html', employee = employee)
   	return f"Employee with id ={id} Does not exist"
   ```

- Function to update a record.

  ```python
  @app.route('/data/<int:id>/update',methods = ['GET','POST'])
  def update(id):
  	employee = EmployeeModel.query.filter_by(employee_id=id).first()
  	if request.method == 'POST':
  		if employee:
  			db.session.delete(employee)
  			db.session.commit()

  			name = request.form['name']
  			age = request.form['age']
  			position = request.form['position']
  			employee = EmployeeModel(employee_id=id, name=name, age=age, position = position)

  			db.session.add(employee)
  			db.session.commit()
  			return redirect(f'/data/{id}')
  		return f"Employee with id = {id} Does not exist"
  	return render_template('update.html', employee = employee)
  ```

 - Function to delete a record.

   ```python
   @app.route('/data/<int:id>/delete', methods=['GET','POST'])
   def delete(id):
   	employee = EmployeeModel.query.filter_by(employee_id=id).first()
    if request.method == 'POST':
        if employee:
            db.session.delete(employee)
            db.session.commit()
            return redirect('/data')
        abort(404)
 
    return render_template('delete.html')
	```

 - Finally, start the app and test it.

4. Create a folder called **templates** to store all the static pages to be rendered.

	**createpage.html**
   ```html
   <form action="" method="POST">
  <p>employee ID <input type="integer" name="employee_id" /></p>
  <p>name <input type="text" name="name" /></p>
  <p>age <input type="integer" name="age" /></p>
  <p>position <input type="text" name="position" /></p>
  <p><input type="submit" value="Submit" /></p>
</form>
   ```

**datalist.html**
   ```html
   {% for employee in employees %}
<h3>{{employee}}</h3><hr>
{% endfor %}
   ```

**data.html**
   ```html
   <h3>Id</h3>
<p>{{employee.employee_id}}</p><hr>
<h3>Name</h3>
<p>{{employee.name}}</p><hr>
<h3>Age</h3>
<p>{{employee.age}}</p><hr>
<h3>Position</h3>
<p>{{employee.position}}</p><hr>
   ```

**update.html**
   ```html
   <form action='' method = "POST">
    <p>name <input type = "text" name = "name" value="{{employee.name}}"/></p>
    <p>age <input type = "integer" name = "age"  value="{{employee.age}}"/></p>
    <p>position <input type = "text" name = "position" value="{{employee.position}}"/></p>
    <p><input type = "submit" value = "Submit" /></p>
  </form>
   ```

	**delete.html**
   ```html
   <form action='' method="post">
    Click YES to confirm
    <input type = "submit" value="YES">
    <a href='/data'>Cancel</a>
</form>
   ```

6. Testing Your API:
   - Run your Flask app (app.run()).
   - Use tools like Postman or your browser to test different endpoints and methods.

## 5.4 Serialize Data with Marshmallow

Reference: (https://medium.com/@jesscsommer/how-to-serialize-and-validate-your-data-with-marshmallow-a815b2276a)

Serialization is the process by which you translate a data structure into another format in order to share or save the data.

One example of this, and what we will focus on in our later walkthroughs, is when you take an instance of a Python class and convert it to JSON.

The process also works in reverse, this time known as deserialization, e.g. when you load JSON data into an instance of a Python class.

**Schema**

We serialize our data by defining schema, or rules for how each data field on a certain model should be represented. You may have heard of this in the context of database schema, where you outline the architecture of your database itself (tables, columns, relationships, etc).

The serialization schema has a similar intention — outline rules for a table or model — except now we are focusing solely on data representation, rather than data storage. We might save four columns for a table to our database, but choose only to display one or two once serialized.

**Defining Marshmallow Schema**

Let’s say we have three models: Users, Reviews, and Books.
- A user has many reviews.
- A review has one user and one book.
- A book has many reviews.

Before we begin, double-check that you have installed Marshmallow and Flask-Marshmallow successfully and configured it for your Flask application.

```python
# import Marshmallow and fields for initial setup
from flask_marshmallow import Marshmallow
from marshmallow import fields 

# set up Marshmallow for your particular Flask app 
app = Flask(__name__)
ma = Marshmallow(app)
```

Now we’ll dive in to creating schema for our Reviews model. To do so, we will create a new Python class that inherits from Marshmallow. Each schema class will include a Meta sub-class where we set our initial settings, prior to creating our field-by-field serialization rules.

```python
# the schema class inherits from Marshmallow SQL Alchemy Schema
class ReviewSchema(ma.SQLAlchemySchema):
    # define schema settings in Meta subclass
    class Meta():
        # set your model equal to your defined model in another file
        # you may need to import the model to this file 
        model = Review
        # allow deserialization to instances of the above model 
        load_instance = True
        # choose which fields to serialize for reviews by default 
        fields = ("id", "rating", "comment", "book", "user")

    # define the expected data type for non-nested fields
    rating = fields.Float(required=True)
    comment = fields.String(required=True) 
    # for nested fields, include the relevant schema for that model 
    # customize the default schema
    # in this case by limiting what you get back with "only"
    book = fields.Nested(BookSchema, only=("id", "title"))
    user = fields.Nested(UserSchema, only=("id", "username"))
```

Once we define our schema, it’s time to test it out and actually display our data. To do this, we instantiate an instance of our schema class, then call Marshmallow’s .dump() method to serialize.

```python
# instantiate an instance of our review schema class
# many=True because we want to serialize a collection of reviews 
reviews_schema = ReviewSchema(many=True)

# deserialize reviews according to the schema defined above
# where reviews is a variable for the rows we want to return from the db
reviews_schema.dump(reviews)
```

The serialized reviews would then appear as follows:

```json
## /reviews

[
     {
        "id": 1,
        "rating": 3.0,
        "comment": "Comment text",
        "book": {
            "id": 1,
            "title": "The Poppy War"
        },
        "user": {
            "id": 1,
            "username": "user123"
        }
    },
    {
        "id": 2,
        "rating": 4.5,
        "comment": "Comment text",
        "book": {
            "id": 2,
            "title": "The Dragon Republic"
        },
        "user": {
            "id": 5,
            "username": "user567"
        }
    }
]
```

