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

5. Create a python file called **models.py** and add this codes.

   ```python
   from flask_sqlalchemy import SQLAlchemy

   db = SQLAlchemy()

   class EmployeeModel(db.Model):
   	__tablename__ = "table"

   	id = db.Column(db.Integer, primary_key=True)
   	employee_id = db.Column(db.Integer(),unique = True)
   	name = db.Column(db.String())
   	age = db.Column(db.Integer())
   	position = db.Column(db.String(80))
 
    def __init__(self, employee_id,name,age,position):
        self.employee_id = employee_id
        self.name = name
        self.age = age
        self.position = position
 
    def __repr__(self):
        return f"{self.name}:{self.employee_id}"
   ```
   
7. Testing Your API:
   - Run your Flask app (app.run()).
   - Use tools like Postman or your browser to test different endpoints and methods.

