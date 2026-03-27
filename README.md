# ComplaintSystem

ComplaintSystem is a role-based Django web application for managing citizen complaints across departments. It supports citizen submissions, admin assignment and analytics, and department-level resolution with status updates, comments, feedback, and escalation tracking.

Repository: `https://github.com/HelloCoderCode/ComplaintSystem.git`

**Features**
1. Role-based access for Citizen, Admin, and Department users.
2. Complaint lifecycle: create, assign, update status, resolve, feedback.
3. Escalation workflow based on configurable days.
4. Admin analytics and PDF report export.
5. Department management: create, edit, and delete departments.

**Tech Stack**
1. Python 3
2. Django 5.2.x
3. SQLite (default)
4. Chart.js (CDN) for analytics charts
5. Pillow for image uploads
6. ReportLab for PDF exports

**Project Structure**
1. `ComplaintSystem/` Django project root
2. `ComplaintSystem/ComplaintSystem/` project settings and URLs
3. `ComplaintSystem/users/` user auth and role routing
4. `ComplaintSystem/complaints/` complaint domain logic
5. `ComplaintSystem/dashboard/` admin and department dashboards
6. `ComplaintSystem/departments/` department models and forms
7. `ComplaintSystem/templates/` shared templates
8. `ComplaintSystem/static/` static assets
9. `ComplaintSystem/media/` uploaded files

**Clone**
```bash
git clone https://github.com/HelloCoderCode//ComplaintSystem.git
cd ComplaintSystem
```

**Setup (Windows)**
```bash
python -m venv env
env\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

**Setup (macOS/Linux)**
```bash
python3 -m venv env
source env/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

**Database Setup**
```bash
cd ComplaintSystem
python manage.py makemigrations
python manage.py migrate
```

**Create Admin User**
```bash
python manage.py createsuperuser
```

**Run Server**
```bash
python manage.py runserver
```

Open the app at:
1. `http://127.0.0.1:8000/`

**Key URLs**
1. Public home: `/`
2. Register: `/register/`
3. Citizen login: `/login/`
4. Org login (Admin/Department): `/org/login/`
5. Admin dashboard: `/complaints/admin/dashboard/`
6. Department dashboard: `/departments/dashboard/`
7. Citizen dashboard: `/complaints/dashboard/`
8. Admin analytics: `/complaints/admin/analytics/`
9. Department list: `/departments/admin/list/`
10. Department create: `/departments/admin/create/`

**How It Works (Workflow)**
1. Citizen registers and logs in.
2. Citizen submits a complaint with category, priority, optional image, and location.
3. Admin reviews all complaints in the admin dashboard.
4. Admin assigns a complaint to a department head.
5. Department head updates status and adds remarks or proof.
6. System escalates overdue complaints based on escalation days.
7. Citizen can view updates, comment, and leave feedback after resolution.
8. Admin can export a PDF report.

**Roles & Access**
1. Citizen: can create complaints, view status, comment, and leave feedback.
2. Admin: can view all complaints, assign/update, manage departments, and view analytics.
3. Department: can view assigned complaints and update status.

**Configuration**
1. `ComplaintSystem/ComplaintSystem/settings.py`
2. `ESCALATION_DAYS` controls escalation threshold (default 5).
3. `MEDIA_ROOT` and `MEDIA_URL` handle uploads.

**Optional Dependencies**
1. `reportlab` is required to generate PDF reports.
2. `pillow` is required for image upload fields.

**Troubleshooting**
1. If images do not upload, ensure `MEDIA_ROOT` exists and the server is running in DEBUG mode.
2. If PDF export fails, install `reportlab`.
3. If migrations fail, delete `db.sqlite3` and run migrations again for a clean setup.

**Notes**
1. This project uses SQLite by default for simplicity.
2. For production, use environment variables and a production-ready database.
