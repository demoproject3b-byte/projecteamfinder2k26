Project Team Finder
Project Team Finder is a Flask-based final year project designed to automatically form balanced student teams based on skills, quiz performance, academic records, interests, project experience, and backlogs. It includes coordinator administration, class management, student registration, quiz-based scoring, guide assignment, team generation, PDF export, student team search, project suggestions, and learning resources.
Features
Coordinator registration with pending approval flow
Management dashboard for coordinator approval/decline
Class creation with class password authentication
Student registration with skill and interest tracking
Skill-based quiz generation with difficulty mapping
Team generation based on weighted compatibility scoring
Guide assignment by project interests and team capacity
Team leader selection using weighted academic and skill factors
Student team search by roll number
Ten default interest-specific suggested projects per category, with descriptions of at least 500 words and database-stored, watermark-free image URLs
100 default learning projects across the interest categories, each linked to related YouTube project tutorials
SQLite database support with automatic initialization
PDF export for generated team lists
Responsive Bootstrap UI
Technology Stack
Python 3.14.6
Flask
SQLite
Bootstrap 5
ReportLab for PDF export
Jinja2 templates
Project Structure
project_team_finder/
├── python/
│   ├── Main.py
│   ├── student.py
│   ├── coordinator.py
│   ├── Management.py
│   ├── schema.py
│   └── Question_bank/
│       ├── init.py
│       ├── Question_bank1.py
│       ├── Question_bank2.py
│       ├── Question_bank3.py
│       ├── Question_bank4.py
│       ├── Question_bank5.py
│       ├── Question_bank6.py
│       └── Question_bank7.py
├── static/
│   ├── css/
│   ├── js/
│   └── images/
├── templates/
├── database/
├── requirements.txt
├── README.md
└── project_team_finder.db (created automatically)
Installation Requirements
Install Python 3.14.6.
Open the project folder in a terminal or IDLE.
Create a virtual environment if needed.
Install dependencies from requirements.txt.
Virtual Environment Setup
Windows PowerShell:
python -m venv venv
.\venv\Scripts\activate
Linux/macOS:
python3 -m venv venv
source venv/bin/activate
Dependency Installation
pip install -r requirements.txt
SQLite Database Setup
The application initializes the SQLite database automatically when the Flask app starts. If the database does not exist, a new database file will be created in the database folder.
Database Initialization
The main initialization occurs in schema.py. The following happens automatically:
Creates required database tables
Adds default admin credentials if absent
Seeds default question banks
Seeds default learning resources and suggested projects
Running the Flask Server
From the project root folder, run:
python python/Main.py
Then open your browser at:
http://127.0.0.1:5000/
Default Management/Admin Setup
The default admin is created automatically from environment variables or fallback values:
Name: admin
Username: admin
Password: admin123
You can set environment variables before starting the app:
set PTF_ADMIN_NAME=admin
set PTF_ADMIN_USERNAME=admin
set PTF_ADMIN_PASSWORD=admin123
Coordinator Registration Workflow
Go to the Home page.
Click Coordinator Login.
Click Register here.
Fill in Coordinator Name, Username, and Password.
Submit the form.
The account status becomes Pending Approval.
Management must approve the coordinator before login is allowed.
Student Registration Workflow
Open the Student Portal.
Enter student details, class name, and class password.
Select relevant skills and skill levels.
Choose project interests.
Submit the form.
The student is redirected to the quiz portal.
Quiz Workflow
The system selects quiz questions based on selected skills and difficulty levels.
The quiz includes at least 10 questions.
Users answer and submit the quiz.
Score is calculated automatically.
Quiz rating is stored in the database and used for team formation.
Team Generation Workflow
Coordinator logs in.
Creates a class.
Registers students under that class.
Adds a guide if needed.
Clicks Generate Teams from the class dashboard.
System uses balancing algorithm with skill match, quiz rating, academic performance, backlog count, project experience, and interests.
Team leader is selected using weighted evaluation.
Teams are stored in the database.
PDF Generation Workflow
On the Teams page, click Print PDF.
This exports the generated team roster as a PDF document containing:
Class name
Team number
Team leader
Team members
Team interest
Guide name
Troubleshooting
Module import error
Check that you are running the app from the correct directory and that the python folder is accessible.
Database not creating
Ensure the database folder exists and that sqlite3 is available in the Python installation.
Cannot log in as coordinator
Make sure the coordinator account is approved by management.
Team generation not working
Check that at least one student is registered and that the class team size is valid.
Quiz not showing questions
Ensure there are question banks seeded correctly and that the skill names match the selected student skills.
Final Notes
This project is designed to be beginner-friendly, modular, and suitable for a Diploma 5th Semester final project demo.
