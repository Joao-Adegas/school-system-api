# Academic Management System API

A complete system for managing professors, courses and room reservations, built with **Django** and **Django REST Framework**.

> Frontend: [school-system-web](https://github.com/Joao-Adegas/school-system-web)

## Objective

Provide a management system where **Managers** can register, update and delete professors, their courses and room reservations. Authentication ensures that only managers can perform these operations, while **Professors** have restricted access to view the information relevant to their activities.

## Features

### Professors
- Register, list, update (contact data and assigned courses) and delete professors

### Courses
- Create courses and link them to professors
- List courses with the responsible professor
- Update details such as name, workload and responsible professor
- Delete courses

### Room reservations
- Create reservations with date, time and room
- List reservations with room, schedule and responsible professor
- Cancel reservations

### Authentication and authorization
- **JWT authentication**
- **Manager profile:** full access to CRUD operations
- **Professor profile:** read-only access to linked courses and reservations

## Data model

**Professor:** id, name, email, phone, birth date, hire date, assigned courses

**Course:** name, program, workload, description, responsible professor (FK)

**Room reservation:** start date, end date, period (morning, afternoon or evening), reserved room, responsible professor (FK), associated course (FK)

## Tech stack

Python, Django, Django REST Framework, MySQL, JWT (simplejwt), Swagger / Postman

## Getting started

### Prerequisites

- Python 3.8+
- MySQL 8.0+
- pip

### 1. Environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

pip install django djangorestframework djangorestframework-simplejwt mysqlclient
```

### 2. Database

```sql
CREATE DATABASE academic_management_system;
CREATE USER 'django_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON academic_management_system.* TO 'django_user'@'localhost';
FLUSH PRIVILEGES;
```

Then set these credentials in `settings.py`.

### 3. Migrations and run

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

## Author

João Pedro dos Santos Adegas — [@Joao-Adegas](https://github.com/Joao-Adegas)
