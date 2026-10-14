========================================================================
                      DJANGO NEWS API CAPSTONE PROJECT
========================================================================

1. PROJECT OVERVIEW
-------------------
This project is a comprehensive full-stack News and Content Management Portal
built with Django and Django REST Framework (DRF), backed by a MariaDB relational
database. It features strict Role-Based Access Control (RBAC), custom web dashboards
for readers, journalists, and editors, automated email notifications, and webhook
event handlers.

## GitHub Repository Link
You can access, fork, or clone the physical repository for testing and deployment
from your GitHub profile:
https://github.com/mcusick001/News-Application.git

--------------------
2. PROJECT STRUCTURE
--------------------
news_project/
│
├── news/
│   ├── migrations/
│   │   |-- __init__.py
│   │   |-- 0001_initial.py
|   |   |-- 0002_publisher_editors_publisher_journalists_and_more.py
|   |   |-- 0003_newsletter_articles.py
|   |   |-- 0004_alter_article_journalist.py
│   ├── templates/
│   │   └── news/
|   |       |-- article_form.html
│   │       |-- base.html
│   │       |-- editor_dashboard.html
│   │       |-- journalist_dashboard.html
│   │       |-- login.html
│   │       |-- newsletter_form.html
│   │       |-- publisher_management.html
│   │       |-- register.html
|   |       |-- subscriptions.html
│   ├── __init__.py
│   ├── admin.py
│   ├── api_views.py
│   ├── apps.py
│   ├── decorators.py
│   ├── forms.py
│   ├── models.py
│   ├── permissions.py 
│   ├── serializers.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
│
├── news_project/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── .gitignore
├── manage.py
├── README.md
└── requirements.txt


3. LOCAL SETUP & INSTALLATION
-----------------------------
1. Clone the repository and navigate into the project directory:
   bash

   git clone [https://github.com/mcusick001/News-Application.git]

   cd News-Application

2. Database Setup (MySQL/MariaDB):
   This project requires a relational database. Follow these commands to
   set up your database.
   1. Open your terminal and log into the MySQL/Maria DB command line
   interface:
   bash

   mysql -u root -p
   (Enter your root password when prompted)

   2. Run the following SQL query to create the project database:
   sql

   CREATE DATABASE news_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

   3. Exist the MySQL command line prompt:
   sql

   EXIT;

3. Create and activate a Python virtual environment:
   python -m venv venv
   venv\Scripts\Activate.ps1

4. Install required dependencies & configure settings:
   1. Install all required project packages:
   bash

   pip install -r requirements.txt

   2. Open your news_project/settings.py and update your
   database configuration details to match your local credentials
   (
      NAME: 'news_db',
      USER: 'root',
      PASSWORD: 'your_password',
      HOST: 'localhost',
      PORT: '3306'
   ).

5. Run database migrations & Create Admin User:
   1. Apply the database migrations to build your tables:
      bash

      python manage.py makemigrations
      python manage.py migrate

   2. Create an administrative superuser account:
      bash

      python manage.py createsuperuser

6. Launch the local development server:
   bash

   python manage.py runserver

7. Accessing the application
   Once the server is running, you can open your web browser and access
   the application at the following endpoints:
   - Home/Login Page: http://127.0.0.1:8000/
   - User Registration: http://127.0.0.1:8000/register/
   - Smart Dashboard Routing: http://127.0.0.1:8000/dashboard/
   (Automatically routes you based on your user role after logging
   in)
   - Django Admin Panel: http://127.0.0.1:8000/admin/
   - REST API Root: http://127.0.0.1:8000/api/

4. AUTOMATED TEST SUITE
-----------------------
The project includes a robust unit test suite (`APITestCase`) in `news/tests.py`
covering authentication, RBAC permissions, webhook mocking, and subscription filtering.

To run the automated tests:

   python manage.py test news
