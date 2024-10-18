# Project_Management

Steps to Run the Project

Pre-requisite(installations) MySQL Server MySQL Workbench

Go to command prompt and install the below requirements

pip install cryptography pip install rest_framework pip install Django

Extract the project_management.zip file

Database Connectivity with MySQL

To configure MySQL as the backend database for a Django application, follow these steps: Step-by-Step Guide:

Install MySQL and Python MySQL Connector: o Ensure that MySQL is installed and running on your system. o Install the Python MySQL client (mysqlclient) which Django uses to
connect to MySQL:

pip install mysqlclient

Alternatively, you can install PyMySQL if mysqlclient causes compatibility issues:

pip install pymysql

Create a MySQL Database: Open the MySQL command-line tool or a database management tool like MySQL and create a database for your Django project:

CREATE DATABASE CRM_db; use CRM_db;

//create a database user and assign them privileges for this database:

CREATE USER 'django_user'@'localhost' IDENTIFIED BY 'password'; GRANT ALL PRIVILEGES ON CRM_DB.* TO 'django_user'@'localhost'; FLUSH PRIVILEGES;

Configure Django to Use MySQL: Update your settings.py in project_management to use MySQL as the database backend.
In the DATABASES section, configure it as follows: python Copy code DATABASES = { 'default': { 'ENGINE': 'django.db.backends.mysql', 'NAME': 'CRM_db_db', # Name of the MySQL database 'USER': 'django_user', # MySQL user 'PASSWORD': 'password', # MySQL user's password 'HOST': 'localhost', # Typically 'localhost' or '127.0.0.1' 'PORT': '3306', # Default MySQL port (3306) } }

Run Migrations to Set Up the Database: Now that Django is configured to use MySQL, you need to create the database schema for your app using migrations in command prompt:
python manage.py migrate

Django will create the necessary tables for its models in your MySQL database. 10. Verify Connection: Start the Django development server and ensure that everything is working as expected:

python manage.py runserver

not create superuser using py manage.py createsuperuser

run project using py manage.py runserver

if you paste above url in browser ,you will get below error

Page not found (404) Request Method: GET Request URL: http://127.0.0.1:8000/ Using the URLconf defined in project_management.urls, Django tried these URL patterns, in this order:

admin/ api/ The empty path didn’t match any of these.

You’re seeing this error because you have DEBUG = True in your Django settings file. Change that to False, and Django will display a standard 404 page.

access the admin panel of Django using http://127.0.0.1:8000/admin

now access the client using http://127.0.0.1:8000/api/clients/

You can access Projects using http://127.0.0.1:8000/api/projects/

For further operation follow as specified routes in clients/urls.py(application urls.py)
