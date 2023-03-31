1. Install flask - pip install flask

2. In linux/mac, export FLASK_APP=blog.py
In windows, set FLASK_APP=blog.py (cmd line) and $env:FLASK_APP = "hello.py" (powershell)

3. export FLASK_DEBUG=1

4. Templating engine = jinja2
5. template inheritance - to separate out common html code in layout file

6. pip install flask-wtf
7. pip install email_validator
8. pip install flask-sqlalchemy
9. magic methods in python like __repr__ for this watch oop in python by the author
10. one to many relationship in SqlAlchemy
example - posts = db.relationship('Post', backref='author', lazy=True)

user_id = db.column(db.Integer, db.ForeignKey(user.id), nullable=False)

The example above means following 
a. The posts attribute has relationship with Post model. 
b. backref is similar to adding another column to the Post model. What the back ref allows us to do is when we have a post we can simply use this author attribute to get the user who created the post. 
c. Lazy argument just defines when SQL Alchemy loads the data from the database so true means that SQL alchemy will load the data as necessary in one go. 

11. To create db do the following 

a. Run python shell - python
b. from blog import app,db
c. app.app_context().push()
d. db.create_all()

This will create database on file system and site.db file in the project directory

12. Add user and post data directly using terminal

from blog import User, Post
user_1 = User(username='Poulomi', email='p@demo.com', password='password')
db.session.add(user_1) - This will not actually add changes unless we commit
user_2 = User(username='PG', email='pg@demo.com', password='password')
db.session.add(user_2) 
db.session.commit()

13. To get all users
User.query.all()

14. Circular import in python

15. Rearrange running python application as a module to package

16. Encrypt password before storing in db - pip install flask_bcrypt

17. validate existing user name and email

18. pip install flask_login to manage db sessions for us

19. validate email and password for login 

20. if current user already logged in keep them logged in

21. create logout link 

22. Add account manager

23. get query params

24. In account page -change layout 

25. In account route - add file validation and saving file function

26. Create , update and delete posts


Manging user session with flask_login 

1. pip install flask-login
2. In init.py from falst_login import LoginManger

login_manager = LoginManager(app)

3. In database models.py file add following 

from blog import db, login_manager
@login_manager.user_loader
def load_user(user_id):
    return User.query.get(int(user_id))

Python tips 

using get method to access dictionary is better so that of the dictionary doesn't we don't get error. 

