# CRM System using Django

## Overview

A Customer Relationship Management system built with Django 5.1.7 for managing customer records with user authentication and CRUD operations.

## Technical Stack

- **Framework**: Django 5.1.7
- **Database**: SQLite3
- **Authentication**: Django built-in authentication system

## Project Structure

```
CRM/                    # Django project configuration
web/                    # Primary application
├── models.py          # Customer Record model
├── views.py           # Business logic
├── forms.py           # Form validation
├── urls.py            # URL patterns
└── templates/         # HTML templates
manage.py              # Django management script
```

## Data Model

```python
class Record(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    email = models.CharField(max_length=100)
    phone = models.CharField(max_length=15)
    address = models.CharField(max_length=100)
    city = models.CharField(max_length=50)
    state = models.CharField(max_length=50)
    zipcode = models.CharField(max_length=20)
```

## Features

- User registration and authentication
- Customer record CRUD operations
- Session-based security
- Form validation

## Installation

1. Install Django:
```bash
pip install django==5.1.7
```

2. Run migrations:
```bash
python manage.py migrate
```

3. Start development server:
```bash
python manage.py runserver
```

## URL Endpoints

- `/` - Home page and record listing
- `/register/` - User registration
- `/logout/` - User logout
- `/record/<int:pk>` - View customer record
- `/add_record/` - Create new record
- `/update_record/<int:pk>` - Update record
- `/delete_record/<int:pk>` - Delete record

## Security Notes

- Authentication required for record operations
- CSRF protection enabled
- Debug mode enabled (development only)