# E-VURA PLATFORM ( [https://evura.onrender.com](https://evura.onrender.com) ) BY **QWERTY TEAM**

---

## Table of Contents

1. Overview & Demo Video
2. Features
3. System Architecture
4. Technologies Used
5. Local Development Setup
6. Deployment Guide
7. User Manual
8. Admin Guide
9. API Documentation
10. Security Features
11. Database Schema
12. Challenges and Solutions
13. Future Enhancements
14. Credits and Acknowledgments

---

## 1. OVERVIEW
### 1.1 System Description

E-Vura is a comprehensive digital healthcare platform designed specifically for Rwanda and African healthcare systems. The platform addresses critical challenges in healthcare delivery by providing seamless medical record continuity, chronic disease management, and efficient doctor-patient connectivity.

**Mission**: To eliminate the problem of lost medical history when patients switch healthcare providers, ensuring complete continuity of care and preventing duplicate expensive tests.

**Vision**: A healthcare system where every patient's complete medical timeline is accessible to any qualified doctor, enabling better diagnosis and treatment outcomes.

**Important Notice**: This platform handles sensitive medical data and implements industry-standard security measures. All medical decisions should be made in consultation with qualified healthcare professionals.

### 1.2 E-vura Demo Video
**Watch full demo video here:** [click here](https://www.youtube.com/@mindfulsolutionsALU)

---

## 2. FEATURES

### 2.1 Patient Management System
- **Complete Registration**: Comprehensive patient profiles with medical history
- **Medical Timeline**: Chronological tracking of all medical events
- **Chronic Disease Management**: Special alerts and continuous monitoring
- **Document Upload**: Support for medical files (X-rays, MRI, lab reports, prescriptions)
- **Cross-Hospital Access**: Medical records accessible to authorized doctors across different hospitals

### 2.2 Doctor Verification and Management
- **Application System**: Pre-verification process before account creation
- **Document Verification**: Rwanda Medical Council (RMDC) license verification
- **Professional Profiles**: Detailed doctor information with specializations
- **Availability Management**: Doctors can set their consultation schedules
- **Patient History Access**: Complete medical timeline access with proper authorization

### 2.3 Appointment Booking System
- **Real-time Availability**: Live availability checking and slot booking
- **Time Slot Management**: 30-minute appointment slots with conflict prevention
- **Email Notifications**: Automated appointment confirmations and updates
- **Status Tracking**: Comprehensive appointment lifecycle management

### 2.4 Administrative Features
- **Doctor Application Review**: Admin panel for verifying doctor credentials
- **Application Notifications**: Real-time alerts for new doctor applications
- **User Management**: Comprehensive user oversight and management tools
- **Security Monitoring**: Login tracking and access management

### 2.5 Communication System
- **Email Integration**: SendGrid-powered email notifications
- **Appointment Alerts**: Automated patient and doctor notifications
- **System Updates**: Important platform announcements and updates

---

## 3. SYSTEM ARCHITECTURE

### 3.1 Backend Architecture
```
Flask Application (Python)
├── Models (SQLAlchemy ORM)
├── Routes (RESTful endpoints)
├── Authentication (Session-based)
├── Email Service (SendGrid)
└── File Management (Secure uploads)
```

### 3.2 Database Design
- **PostgreSQL** production database
- **SQLite** development database
- **Relationship mapping** between patients, doctors, appointments, and medical records
- **Data integrity** with foreign key constraints

### 3.3 Security Layer
- **Password hashing** with Bcrypt
- **Session management** for authentication
- **Role-based access control** (Patient/Doctor/Admin)
- **File upload validation** and secure storage

---

## 4. TECHNOLOGIES USED

### 4.1 Backend Technologies
- **Python 3.13**: Core programming language
- **Flask**: Web application framework
- **SQLAlchemy**: Object-Relational Mapping (ORM)
- **Flask-Bcrypt**: Password hashing and security
- **Werkzeug**: WSGI utilities and file handling

### 4.2 Database
- **PostgreSQL**: Production database (Render)
- **SQLite**: Development and testing database

### 4.3 Frontend Technologies
- **HTML5**: Markup and structure
- **CSS3**: Styling and responsive design
- **JavaScript**: Interactive functionality
- **Tailwind CSS**: Utility-first CSS framework

### 4.4 External Services
- **SendGrid**: Email delivery service
- **Render**: Cloud hosting platform
- **GitHub**: Version control and deployment

### 4.5 Development Tools
- **Git**: Version control system
- **VS Code**: Development environment
- **Local browser**: API endpoints testing (development phase)

---

## 5. LOCAL DEVELOPMENT SETUP

### 5.1 Prerequisites
- Python 3.9 or higher
- Git version control
- Text editor or IDE (VS Code recommended)

### 5.2 Installation Steps

**Step 1: Clone the Repository**
```bash
git clone https://github.com/e-vura/E-vura.git
cd E-vura
```

**Step 2: Create Virtual Environment**
```bash
python -m venv venv or virtualenv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

**Step 3: Install Dependencies**
```bash
    pip install -r requirements.txt
```

**Step 4: Environment Configuration**
Create a `.env` file in the root directory:
```env
SENDGRID_API_KEY=insert_sendgrid_api_key_here
DATABASE_URL=sqlite:///evura.db
SECRET_KEY=secret_key_holder
```

**Step 5: Initialize Database**
```bash
python app.py
# Database tables will be created automatically on first run
```
If failed to run consider the following option:
```bash
#open the terminal and go inside python environment and follow the following manually
python
>>> from app import app, db
>>> with app.app_context():
      db.create_all()
...
>>>exit() # to go back to normal evironment
```


**Step 6: Run the Application**
```bash
python app.py
# Access the app at http://localhost:5000
```

### 5.3 Development Database Setup
The application automatically creates necessary database tables on startup. For testing purposes, you can use the `/reset-db` route to clear and recreate the database.

---

## 6. DEPLOYMENT GUIDE

### 6.1 Render Cloud Deployment

**Prerequisites:**
- GitHub account
- Render account
- SendGrid account for email services

**Step 1: Repository Setup**
- Push code to GitHub repository
- Ensure `requirements.txt` includes all dependencies:
```txt
bcrypt==5.0.0
blinker==1.9.0
click==8.3.0
colorama==0.4.6
Flask==3.1.2
Flask-Bcrypt==1.0.1
Flask-Login==0.6.3
Flask-SQLAlchemy==3.1.1
Flask-WTF==1.2.2
greenlet==3.2.4
gunicorn==23.0.0
itsdangerous==2.2.0
Jinja2==3.1.6
MarkupSafe==3.0.3
packaging==25.0
SQLAlchemy==2.0.44
typing_extensions==4.15.0
Werkzeug==3.1.3
WTForms==3.2.1
psycopg2
sendgrid
```

**Step 2: Database Setup**
- Create PostgreSQL database on Render
- Note connection details for environment variables

**Step 3: Web Service Deployment**
- Connect GitHub repository to Render
- Set build command: `pip install -r requirements.txt`
- Set start command: `python app.py`
- Configure environment variables:
  - `SENDGRID_API_KEY`
  - `DATABASE_URL` (PostgreSQL connection string)
  - `SECRET_KEY`

### 6.2 Environment Variables Configuration
```env
SENDGRID_API_KEY=sendgrid_api_key
DATABASE_URL=postgresql_External_URL
SECRET_KEY=secret_key
PORT=5000
```

---

## 7. USER MANUAL

### 7.1 Patient Registration and Setup

**Creating an Account:**
1. Visit the E-Vura homepage
2. Click "Register as Patient"
3. Fill in personal information:
   - Full name
   - Email address
   - Secure password (minimum 6 characters)
4. Accept terms of service
5. Click "Create Patient Account"
6. Check email for confirmation

**Completing Your Profile:**
1. Log in to your account
2. Navigate to "My Profile"
3. Add essential information:
   - Date of birth
   - Blood type
   - Allergies (if any)
   - Chronic conditions
   - Emergency contact
4. Save your profile

### 7.2 Managing Medical Records

**Uploading Medical Files:**
1. Go to "Medical Records" section
2. Click "Upload New Record"
3. Select file type (X-ray, MRI, Lab Report, etc.)
4. Choose file and add description
5. Specify test date and hospital
6. Mark as chronic-related if applicable
7. Upload file

**Viewing Medical Timeline:**
1. Access "Medical Records"
2. Use filter tabs to view specific record types
3. Click on any record for detailed information
4. Download files as needed

### 7.3 Booking Appointments

**Finding and Booking with Doctors:**
1. Navigate to "Find Doctors"
2. Browse available doctors by specialization
3. Click "View Available Times" for your preferred doctor
4. Select date from available options
5. Choose time slot
6. Provide consultation reason
7. Confirm booking
8. Receive email confirmation

**Managing Your Appointments:**
1. View appointments in "My Dashboard"
2. Check appointment status (pending, confirmed, completed)
3. Receive email updates for status changes

---

## 8. ADMIN GUIDE

### 8.1 Doctor Application Review Process

**Accessing Admin Panel:**
1. Navigate to `/admin/login`
2. Enter admin password
3. Access applications dashboard

**Reviewing Applications:**
1. Review pending doctor applications
2. Verify submitted documents:
   - RMDC license number
   - Medical degree certificates
   - Hospital employment verification
3. Check professional information
4. Click "View Document" to examine uploaded files

**Approval Process:**
1. Click "Approve Application" for qualified candidates
2. Confirm approval (creates doctor account automatically)
3. System sends welcome email with login instructions
4. Doctor can immediately log in with application credentials

**Rejection Process:**
1. Click "Reject Application" for unqualified applicants
2. System sends notification email to applicant
3. Application marked as rejected in system

### 8.2 System Administration

**Monitoring Platform Usage:**
- Track daily application submissions
- Monitor approved vs rejected applications
- Review system performance metrics

**Security Management:**
- Change admin password regularly
- Monitor login activities
- Review user access patterns

---


## 9. SECURITY FEATURES

### 10.1 Authentication Security
- **Password Hashing**: Bcrypt with salt for secure password storage
- **Session Management**: Secure session handling with timeout
- **Role-Based Access**: Strict separation of patient, doctor, and admin access

### 9.2 Data Protection
- **Input Validation**: Server-side validation for all user inputs
- **File Upload Security**: Restricted file types and size limits
- **SQL Injection Protection**: SQLAlchemy ORM prevents injection attacks

### 9.3 Privacy Compliance
- **Medical Record Access Control**: Doctors can only access records of patients they have treated
- **Chronic Condition Alerts**: Special handling for sensitive medical information
- **Audit Trail**: Tracking of medical record access and modifications

---

## 10. DATABASE SCHEMA

### 10.1 Core Tables in summary

**Patients Table**
- id (Primary Key)
- username, email, password (hashed)
- phone, date_of_birth, address
- blood_type, allergies, chronic_conditions
- emergency_contact, created_at

**Doctors Table**
- id (Primary Key)
- username, email, password (hashed)
- specialization, hospital, license_number
- years_experience, created_at

**Appointments Table**
- id (Primary Key)
- patient_id (Foreign Key → Patients)
- doctor_id (Foreign Key → Doctors)
- date, time, reason, status
- notes, created_at

### 11.2 Medical Records Tables

**Medical Files Table**
- Patient medical document uploads
- File metadata and categorization
- Chronic condition tracking

**Test Results Table**
- Structured lab and diagnostic results
- Normal ranges and interpretations

**Prescriptions Table**
- Medication history and effectiveness tracking
- Dosage and duration information

**Procedures Table**
- Surgical and medical procedures
- Outcomes and complications tracking

The attached is the erd design: <img width="668" height="2041" alt="evura_diagram" src="https://github.com/user-attachments/assets/6225852b-ba0f-4307-927f-6e490239ac45" />


---

## 12. CHALLENGES AND SOLUTIONS

### 12.1 Database Migration Challenge
**Challenge**: Moving from SQLite development to PostgreSQL production
**Solution**: Implemented environment-based database URL configuration with automatic table creation

### 12.2 Email Service Integration
**Challenge**: Reliable email delivery for appointment notifications
**Solution**: SendGrid integration with comprehensive error handling and logging

### 12.3 File Upload Security
**Challenge**: Secure handling of medical document uploads
**Solution**: File type validation, secure filename generation, and restricted access controls

### 12.4 Doctor Verification Process
**Challenge**: Ensuring only qualified medical professionals gain access
**Solution**: Pre-approval application system with document verification and admin review

### 12.5 Medical Record Privacy
**Challenge**: Balancing accessibility with privacy protection
**Solution**: Permission-based access system where doctors can only view records of patients they have treated

### 12.6 Appointment Scheduling Conflicts
**Challenge**: Preventing double-booking and managing doctor availability
**Solution**: Real-time availability checking with database constraints and time slot management

---

## 13. FUTURE ENHANCEMENTS

### 13.1 Planned Features
- **Mobile Application**: Native iOS and Android applications
- **Telemedicine Integration**: Video consultation capabilities
- **AI-Powered Insights**: Medical history analysis and health predictions
- **Multi-language Support**: Kinyarwanda, French, and English interfaces
- **Insurance Integration**: Health insurance verification and billing

### 13.2 Technical Improvements
- **API Development**: RESTful API for third-party integrations
- **Performance Optimization**: Database indexing and query optimization
- **Advanced Analytics**: Platform usage analytics and health insights
- **Blockchain Integration**: Immutable medical record storage

---

## 14. CREDITS AND ACKNOWLEDGMENTS

### 14.1 Development Team (QWERTY Team)
- **Steven Kayitare**: [https://github.com/stevenalu](https://github.com/stevenalu)
- **Robert Cyubahiro**: [https://github.com/rcyubahiro](https://github.com/rcyubahiro)
- **Belyse Kalisa Teta Yakamwate**: [https://github.com/kbelyse](https://github.com/kbelyse)
- **Rolande Tumugane**: [https://github.com/TRolande](https://github.com/TRolande)
- **Kenny Yannick Imanzi**: [https://github.com/kimanzialu](https://github.com/kimanzialu)
- **Innocent Nkurunziza**: [https://github.com/innocent-gift](https://github.com/innocent-gift)
- **Armstrong Ngororano**: [https://github.com/capitale1](https://github.com/capitale1)

### 14.2 Technologies and Services
- **Flask Framework**: Python web development framework
- **SendGrid**: Email delivery service for notifications
- **Render**: Cloud hosting platform for deployment
- **PostgreSQL**: Reliable database management system

### 14.3 Healthcare Inspiration
This platform was inspired by real story faced by patient with chronic conditions who lose medical history when switching healthcare providers in Rwanda and across Africa.

### 14.4 Special Recognition
- **Rwanda Medical and Dental Council**: For providing medical licensing standards
- **African Leadership University**: For providing educational context and support
- **Open Source Community**: For the foundational technologies that made this platform possible

---

**Contact Information:**
- **Platform URL**: [E-vura](https://evura.onrender.com)
- **Support Email**: [s.kayitare@alustudent.com](mailto:s.kayitare@alustudent.com)

**Disclaimer**: This project is developed for educational and healthcare improvement purposes.
