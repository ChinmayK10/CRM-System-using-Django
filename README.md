# CRM System using Django

## Overview

A Customer Relationship Management (CRM) system built with Django 5.1.7, providing core functionality for managing customer records with user authentication and CRUD operations.

## Technical Architecture

### Framework and Version
- **Django**: 5.1.7
- **Python**: 3.x (compatible)
- **Database**: SQLite3 (development)

### Project Structure

```
CRM-System-using-Django/
├── CRM/                    # Django project configuration
│   ├── settings.py         # Application settings and configuration
│   ├── urls.py            # Main URL routing
│   ├── wsgi.py            # WSGI application entry point
│   └── asgi.py            # ASGI application entry point
├── web/                   # Primary Django application
│   ├── models.py          # Data models
│   ├── views.py           # Business logic and request handling
│   ├── forms.py           # Form definitions and validation
│   ├── urls.py            # Application-specific URL patterns
│   ├── admin.py           # Django admin configuration
│   ├── templates/         # HTML templates
│   └── migrations/        # Database migration files
├── manage.py              # Django management script
└── db.sqlite3            # SQLite database file
```

## Data Model

### Record Model
The core data entity representing customer information:

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

## Application Features

### Authentication System
- User registration with form validation
- Login/logout functionality
- Session-based authentication
- Password validation enforcement

### Customer Record Management
- **Create**: Add new customer records
- **Read**: View individual customer details
- **Update**: Modify existing customer information
- **Delete**: Remove customer records
- **List**: Display all customer records (authenticated users only)

### Security Features
- CSRF protection enabled
- Authentication required for sensitive operations
- Session management
- XFrame protection

## URL Routing

### Main Application Routes
- `/` - Home page with customer record listing
- `/register/` - User registration
- `/logout/` - User logout
- `/record/<int:pk>` - Individual customer record view
- `/add_record/` - Create new customer record
- `/update_record/<int:pk>` - Update existing customer record
- `/delete_record/<int:pk>` - Delete customer record
- `/admin/` - Django administration interface

## Installation and Setup

### Prerequisites
- Python 3.x
- Django 5.1.7

### Installation Steps

1. Clone the repository:
```bash
git clone <repository-url>
cd CRM-System-using-Django
```

2. Install Django (if not already installed):
```bash
pip install django==5.1.7
```

3. Apply database migrations:
```bash
python manage.py migrate
```

4. Create a superuser (optional):
```bash
python manage.py createsuperuser
```

5. Run the development server:
```bash
python manage.py runserver
```

The application will be accessible at `http://127.0.0.1:8000/`

## Configuration

### Database Configuration
- **Engine**: SQLite3 (default)
- **Location**: `db.sqlite3` in project root
- **Migrations**: Managed through Django ORM

### Template Configuration
- **Template Directory**: `templates/` within project base directory
- **Template Engine**: Django Template Language (DTL)
- **Static Files**: Configured for `/static/` URL pattern

### Security Settings
- **Debug Mode**: Enabled (development only)
- **Secret Key**: Configured (should be changed for production)
- **Allowed Hosts**: Currently unrestricted (development configuration)

## Form Validation

### User Registration Form
- Username validation (150 characters maximum)
- Email field validation
- Password confirmation
- Custom Bootstrap styling

### Customer Record Form
- Required field validation for all customer data
- Form field styling with Bootstrap classes
- Input placeholder text for user guidance

## Dependencies

### Core Dependencies
- Django 5.1.7
- Python standard library modules

### Middleware Stack
- SecurityMiddleware
- SessionMiddleware
- CommonMiddleware
- CsrfViewMiddleware
- AuthenticationMiddleware
- MessageMiddleware
- ClickjackingMiddleware

## Development Notes

### Database Considerations
- SQLite3 is suitable for development and small-scale deployments
- For production, consider PostgreSQL or MySQL
- Database migrations should be applied after model changes

### Security Considerations
- Secret key should be environment-specific
- Debug mode must be disabled in production
- Allowed hosts should be restricted in production
- Consider implementing additional authentication measures for production use

### Template System
- Bootstrap integration for responsive design
- Modular template structure with base template inheritance
- Message framework integration for user feedback

## API Endpoints

The application follows RESTful principles for customer record management:
- GET `/` - List all records
- GET `/record/<id>` - Retrieve specific record
- POST `/add_record/` - Create new record
- POST `/update_record/<id>` - Update existing record
- POST `/delete_record/<id>` - Delete record

## Testing

Test files are included in the `web/tests.py` module. Run tests using:
```bash
python manage.py test
```

## Production Deployment Considerations

1. Set `DEBUG = False` in settings
2. Configure appropriate `ALLOWED_HOSTS`
3. Use environment variables for sensitive configuration
4. Implement proper database backup strategies
5. Configure static file serving
6. Set up proper logging configuration
7. Implement SSL/TLS encryption
8. Consider implementing API rate limiting