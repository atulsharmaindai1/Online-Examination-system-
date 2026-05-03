# Online Examination System

A comprehensive web-based examination platform built with PHP, MySQL, Bootstrap, and JavaScript. This system allows teachers to create and manage exams, while students can take exams with real-time monitoring and proctoring features.

# this is hosted link
 https://onlineexaminationatul.lovestoblog.com

## 🚀 Features

### For Teachers
- **Secure Login System** - Password-protected teacher accounts
- **Exam Management** - Create, edit, and delete exams with multiple-choice questions
- **Student Management** - Add and view student records
- **Real-time Monitoring** - Activity tracking during exams
- **Analytics Dashboard** - Comprehensive analytics with charts and performance metrics
- **Results Management** - View detailed exam results and student performance
- **Anti-cheating Features** - Tab switching detection and inactivity monitoring

### For Students
- **User-friendly Dashboard** - Clean interface showing available exams and results
- **Real-time Exam Timer** - Automatic submission when time expires
- **Detailed Results** - Comprehensive result pages with performance analysis
- **Progress Tracking** - Visual progress indicators and countdown timers
- **Secure Exam Environment** - Activity restrictions and exam integrity checks

### System Features
- **Responsive Design** - Works on desktop
- **Real-time Updates** - Live monitoring and status updates
- **Data Visualization** - Charts and graphs for performance analytics
- **Security Features** - Session management and input validation
- **Modern UI/UX** - Beautiful gradient backgrounds and card-based layouts

## 🛠️ Technology Stack

- **Backend**: PHP 7+
- **Database**: MySQL
- **Frontend**: HTML5, CSS3, Bootstrap 5, JavaScript
- **Charts**: Chart.js
- **Icons**: Font Awesome 6

## 📁 Project Structure

```
Online-Examnation-System/
├── Camera-System               #for Camera Mangae  
│   ├── Uplods                  #Store Image inside
│   └── Uplods.php              #Manage the Live Image 
├── index.php                   # Homepage
├── footer.html                 # footer and scripts
├── Teacher /                   # Teacher panel
│   ├── Teacher_Registration.php #for Register in systme
│   ├── Forgot_password.php      #Forgot password
│   ├── teacher_login.php       # Teacher login
│   ├── teacher_dashboard.php   # Teacher dashboard
│   ├── Teacher_nav.php         # teacher navbaar
│   ├── setting.php             # prasnal Information change
│   ├── Create_Exam.php         # Create new exams
│   ├── manage_exam.php          # Edit existing exams
│   ├── view_result.php          # View exam results
│   ├── analytics.php            # Live monitoring
│   ├── system_analytics.php    # Analytics dashboard
│   ├── addStudent.php          # Add students
│   ├── view_students.php        # View student list
│   ├── delete_exam.php          # Delete exams
│   ├── monitor_data.php         # AJAX data for monitoring
│   ├── Teacher_Logout.php             # For Logout
│   ├── terminate.php        # Terminate student exam
│   └── conection.php        # Database connection
└── Student/                 # Student panel
    ├── Student_Login.php     # Student login
    ├── student_dashboard.php  # Student dashboard
    ├── nav_student.php        #for Student navbaar
    ├── exam.php             # Exam interface
    ├── result.php           # Individual result page
    ├── full_results.php     # All results page
    ├── submit_exam.php      # Exam submission
    ├── logout.php           # Student logout
    ├── activity.php         # Activity tracking
    └── check_terminate.php  # Check termination
```

## 🗄️ Database Schema

### Tables Required:
- `teachers` - Teacher accounts
- `students` - Student accounts
- `exams` - Exam information
- `questions` - Exam questions
- `results` - Exam results
- `activity` - Student activity during exams
- `alerts` - Proctoring alerts

### Sample SQL:
```sql
CREATE TABLE teachers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255)
);

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    password VARCHAR(255),
    teacher_id INT
);

CREATE TABLE exams (
    id INT PRIMARY KEY AUTO_INCREMENT,
    teacher_id INT,
    exam_name VARCHAR(200),
    exam_date DATE,
    start_time TIME,
    duration INT,
    FOREIGN KEY (teacher_id) REFERENCES teachers(id)
);

CREATE TABLE questions (
    id INT PRIMARY KEY AUTO_INCREMENT,
    exam_id INT,
    question TEXT,
    option1 VARCHAR(500),
    option2 VARCHAR(500),
    option3 VARCHAR(500),
    option4 VARCHAR(500),
    correct_option INT,
    FOREIGN KEY (exam_id) REFERENCES exams(id)
);

CREATE TABLE results (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    exam_id INT,
    score INT,
    total_questions INT,
    submitted_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (exam_id) REFERENCES exams(id)
);

CREATE TABLE activity (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    exam_id INT,
    warnings INT DEFAULT 0,
    terminated BOOLEAN DEFAULT FALSE,
    last_activity TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (exam_id) REFERENCES exams(id)
);

CREATE TABLE alerts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    exam_id INT,
    message TEXT,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (exam_id) REFERENCES exams(id)
);

```

## 🚀 Installation & Setup

## Prerequisites:
   - XAMPP/WAMP or any PHP server
   - MySQL database
   - Web browser with JavaScript enabled


Follow these steps to run the project on your system:

### Step 1: Install Server

Download and install XAMPP or WAMP server.

### Step 2: Copy Project Files

* Extract the project folder (if zipped)
* Copy the folder into:

  * For XAMPP → `C:\xampp\htdocs\`
  * For WAMP → `C:\wamp\www\`

### Step 3: Start Server

* Open XAMPP/WAMP Control Panel
* Start:

  * Apache
  * MySQL

### Step 4: Setup Database

1. Open browser and go to: `http://localhost/phpmyadmin`
2. Click on **New** → Create a database (e.g., `online_exam`)
3. Select the database
4. Click **Import**
5. Choose the `.sql` file from the **Database** folder
6. Click **Go**

### Step 5: Run the Project

* Open browser
* Go to:
  `http://localhost/Online-Examnation-System`

### Step 6: Login (if required)

Use the login credentials provided in this README file.

---

### Important Notes:

* Make sure Apache and MySQL are running
* Do not change database name unless updated in config file
* Use modern browser (Chrome/Edge)
* If error occurs, check database connection file

---


## Default Access:
   - **Homepage**: `http://localhost/Online-Examnation-System/`
   - **Teacher Login**: `http://localhost/Online-Examnation-System/Teacher/teacher_login.php`
   - **Student Login**: `http://localhost/Online-Examnation-System/Student/Student_Login.php`

##  Security Features

- Password hashing with PHP's `password_hash()`
- Session-based authentication
- Input validation and sanitization
- SQL injection prevention with prepared statements
- XSS protection
- CSRF protection on forms

## 📱 Responsive Design

The system is responsive and works on:
- Desktop computers
- Tablets

## 🎨 UI/UX Features

- Modern gradient backgrounds
- Card-based layouts
- Smooth animations and transitions
- Intuitive navigation
- Color-coded status indicators
- Progress bars and visual feedback
- Mobile-friendly touch interfaces

## 🔍 Monitoring & Proctoring

- **Tab Switching Detection**: Alerts when students switch tabs
- **Inactivity Monitoring**: Detects when students are away
- **Activity Logging**: Tracks all student actions
- **Live Alerts**: Real-time notifications to teachers
- **Auto-termination**: Ability to end exams remotely

## 📊 Analytics & Reporting

- **Performance Charts**: Visual representation of results
- **Student Rankings**: Leaderboards and comparisons
- **Pass/Fail Statistics**: Success rate analysis
- **Time-based Analytics**: Performance over time
- **Detailed Reports**: Individual and group insights

## 🔧 Customization Options

- **Themes**: Easily customizable color schemes
- **Question Types**: Extensible for different question formats
- **Time Limits**: Configurable exam durations
- **Scoring Systems**: Flexible grading options
- **Notification Settings**: Customizable alerts and messages

## 🐛 Troubleshooting

### Common Issues:
1. **Database Connection Errors**: Check database credentials and server status
2. **Browser Permission Issues**: Ensure the browser has access to required features and no extensions block execution
3. **JavaScript Errors**: Check browser console, ensure all files are loaded
4. **Session Issues**: Clear browser cookies, check PHP session configuration

### Debug Mode:
- Enable error reporting in PHP for development
- Check browser developer tools for JavaScript errors
- Monitor network requests for AJAX calls






