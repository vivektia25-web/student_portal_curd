# 🧑‍🎓 Student LMS Portal – Django Project

A simple, stylish **Student LMS (Learning Management System)** web application built with **Django**. This system allows users to add, view, search, edit, and delete student records, styled with pure CSS and responsive layout.

---

## ✨ Features

- 📥 **Add Student**: Save student details into the database.
- 🔍 **Search Student**: Lookup students by Student ID.
- 📋 **View All Students**: Display all student records in a styled table with Edit/Delete options.
- ✏️ **Edit Student**: Update existing student information.
- 🗑️ **Delete Student**: Remove a student from the system (from form or inline in the table).
- 🎨 **Styled UI**: Responsive interface using only custom CSS with background image support.

---

## 🚀 Technologies Used

- **Python 3.10+**
- **Django 5.2+**
- **HTML5 & CSS3**
- **SQLite** (default Django DB)
- **Gunicorn** (production server)

---

## 🏗️ Project Structure

```
student_portal_crud/
├── manage.py                      # Django management script
├── db.sqlite3                     # SQLite database
├── requirements.txt               # Python dependencies
├── README.md                      # Project documentation
│
├── student_portal/                # Main project configuration
│   ├── __init__.py
│   ├── settings.py               # Django settings
│   ├── urls.py                   # Main URL routing
│   ├── asgi.py                   # ASGI configuration
│   └── wsgi.py                   # WSGI configuration
│
└── lms/                           # LMS app (main application)
    ├── __init__.py
    ├── models.py                 # Database models (Student)
    ├── views.py                  # View functions (CRUD operations)
    ├── urls.py                   # App URL routing
    ├── forms.py                  # Django forms
    ├── admin.py                  # Django admin configuration
    ├── apps.py                   # App configuration
    ├── tests.py                  # Unit tests
    ├── migrations/               # Database migrations
    ├── static/lms/               # Static files (CSS, JS, images)
    │   └── styles.css           # Main stylesheet
    └── templates/lms/            # HTML templates
        ├── base.html             # Base template
        ├── home.html             # Homepage
        ├── add_student.html      # Add student form
        ├── edit_student.html     # Edit student form
        ├── delete_student.html   # Delete student form
        ├── search_student.html   # Search student form
        └── view_students.html    # View all students
```

---

## 💾 Database Model

**Student Model** (in [lms/models.py](lms/models.py)):
- `student_id` (CharField, Unique): Unique student identifier
- `name` (CharField): Student's full name
- `email` (EmailField): Student's email address
- `course` (CharField): Course enrolled in

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed:
- **Python 3.10+** - [Download](https://www.python.org/downloads/)
- **pip** - Python package manager (included with Python)
- **Git** (optional, for version control)

---

## 📝 Installation Guide

### Step 1: Clone/Download the Repository

```bash
git clone https://github.com/your-username/student_portal_crud.git
cd student_portal_crud
```

Or download the ZIP file and extract it.

### Step 2: Create a Virtual Environment

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

**Required packages:**
- `django` - Web framework
- `gunicorn` - Production server
- `psycopg2-binary` - PostgreSQL adapter (optional, if using PostgreSQL)
- `whitenoise` - Static files handling

### Step 4: Apply Database Migrations

```bash
python manage.py migrate
```

This creates the SQLite database and applies all migrations.

### Step 5: Create a Superuser (Admin Account)

```bash
python manage.py createsuperuser
```

Follow the prompts to create an admin account:
```
Username: admin
Email: admin@example.com
Password: ****
Password (again): ****
```

---

## 🚀 Running the Application Locally

### Start the Development Server

```bash
python manage.py runserver
```

Output:
```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
July 14, 2026 - 12:00:00
Django version 5.2, using settings 'student_portal.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

### Access the Application

- **Application Homepage**: http://localhost:8000/
- **Django Admin Panel**: http://localhost:8000/admin/
  - Login with the superuser credentials you created

---

## 🧪 Testing Guide

### 1. **Homepage Test**
- Navigate to: http://localhost:8000/
- **Expected Result**: Homepage displays with navigation menu

### 2. **Add Student Test**
- Click on "Add Student" or navigate to: http://localhost:8000/add/
- Fill in the form:
  - **Student ID**: `STU001`
  - **Name**: `John Doe`
  - **Email**: `john@example.com`
  - **Course**: `Computer Science`
- Click **Submit**
- **Expected Result**: Success message displays, form clears

### 3. **View All Students Test**
- Navigate to: http://localhost:8000/students/
- **Expected Result**: Table displays all added students with Edit/Delete buttons

### 4. **Search Student Test**
- Navigate to: http://localhost:8000/search/
- Enter Student ID: `STU001`
- Click **Search**
- **Expected Result**: Student details display (or "Not Found" if student doesn't exist)

### 5. **Edit Student Test**
- Go to "View Students": http://localhost:8000/students/
- Click **Edit** button on any student
- Modify the student details
- Click **Update**
- **Expected Result**: Student information updated, redirects to view students page

### 6. **Delete Student Test**
- **Option A**: From "View Students" page
  - Click **Delete** button on a student
  - **Expected Result**: Student removed from table

- **Option B**: From "Delete Student" form
  - Navigate to: http://localhost:8000/delete/
  - Enter Student ID
  - Click **Delete**
  - **Expected Result**: Success/Error message displays

### 7. **Admin Panel Test**
- Navigate to: http://localhost:8000/admin/
- Login with superuser credentials
- View/Add/Edit/Delete students from Django admin
- **Expected Result**: All CRUD operations work smoothly

---

## 📋 URL Endpoints Reference

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/` | GET | Homepage |
| `/add/` | GET, POST | Add new student |
| `/students/` | GET | View all students |
| `/students/edit/<id>/` | GET, POST | Edit student by ID |
| `/students/delete/<id>/` | POST | Delete student by ID |
| `/search/` | GET, POST | Search student by ID |
| `/delete/` | GET, POST | Delete via form submission |
| `/admin/` | GET, POST | Django admin panel |

---

## ✅ Verification Checklist

- [ ] Python 3.10+ is installed
- [ ] Virtual environment created and activated
- [ ] Dependencies installed from requirements.txt
- [ ] Database migrations applied successfully
- [ ] Superuser account created
- [ ] Development server runs without errors
- [ ] Homepage loads at http://localhost:8000/
- [ ] Can add a student successfully
- [ ] Can view all students
- [ ] Can search for a student
- [ ] Can edit a student
- [ ] Can delete a student
- [ ] Admin panel accessible and functional

---

## 🐛 Troubleshooting

### Issue: `ModuleNotFoundError: No module named 'django'`
**Solution**: Ensure virtual environment is activated and dependencies are installed:
```bash
pip install -r requirements.txt
```

### Issue: `No such table: lms_student`
**Solution**: Apply migrations:
```bash
python manage.py migrate
```

### Issue: Static files not loading (CSS looks broken)
**Solution**: Collect static files:
```bash
python manage.py collectstatic --noinput
```

### Issue: Port 8000 already in use
**Solution**: Run on a different port:
```bash
python manage.py runserver 8080
```

### Issue: Database locked error
**Solution**: Delete `db.sqlite3` and recreate:
```bash
rm db.sqlite3
python manage.py migrate
python manage.py createsuperuser
```

---

## 📦 Production Deployment

For production deployment on platforms like **Render** or **Heroku**:

1. Set `DEBUG = False` in [student_portal/settings.py](student_portal/settings.py)
2. Update `ALLOWED_HOSTS` with your domain
3. Use Gunicorn to run:
   ```bash
   gunicorn student_portal.wsgi:application
   ```
4. Ensure `whitenoise` is configured for static files

---

## 📚 Additional Resources

- [Django Documentation](https://docs.djangoproject.com/)
- [Django Models Documentation](https://docs.djangoproject.com/en/5.2/topics/db/models/)
- [Django Views Documentation](https://docs.djangoproject.com/en/5.2/topics/http/views/)
- [Django Forms Documentation](https://docs.djangoproject.com/en/5.2/topics/forms/)

---

## 📝 License

This project is open source and available under the MIT License.

---

## 👨‍💼 Support

For issues, questions, or contributions, please open an issue on GitHub or contact the project maintainers.
