# miniproject
operating systems, mini project


Student Schedule Management System
Overview
This project is a web-based application designed to manage and display student schedules using Flask, PostgreSQL, and Docker. The application enables dynamic interaction with a PostgreSQL database to store and retrieve student schedule data and provides a user-friendly interface for viewing schedules.

Key Features
A web interface built with Flask to display student schedules dynamically.
A PostgreSQL database to store and manage course and schedule data.
Fully containerized with Docker for portability and ease of deployment.
Dynamic templates using Jinja2 to render schedule data in a readable and interactive format.
Technologies Used
1. Flask
A lightweight web framework for building the application backend.
Handles routing and rendering of templates (e.g., index.html, timetable.html).
Integrates with PostgreSQL to retrieve and display student schedules dynamically.
2. PostgreSQL
Relational database used to store student data, schedules, courses, and related information.
Structured queries (SELECT, INSERT, etc.) were used to interact with the database.
Table StudentSchedule was created to manage course details, including:
course_title
instructor
day
time
room and other relevant fields.
3. Docker
Docker is used to containerize the application and database, ensuring consistent deployment across environments.
A Dockerfile is included to build the Flask application image.
The PostgreSQL database runs in a separate container, and both containers are orchestrated using Docker.
Project Structure
plaintext
Copy code
docker_mini_project/
│
├── app.py                 # Flask application
├── Dockerfile             # Docker configuration for Flask app
├── requirements.txt       # Python dependencies
├── templates/
│   ├── index.html         # Homepage template
│   └── timetable.html     # Timetable display template
├── venv/                  # Virtual environment for development
├── SQL_queries/           # Contains SQL scripts for creating tables and inserting data
└── README.md              # Project documentation
How to Run
Prerequisites
Python (3.8 or later)
Docker and Docker Compose installed
PostgreSQL installed (optional for local testing)
Steps
1. Clone the Repository
bash
Copy code
git clone https://github.com/your-username/docker_mini_project.git
cd docker_mini_project
2. Build and Run with Docker
Build the Docker image for the Flask application:

bash
Copy code
docker build -t flask-app .
Run PostgreSQL in a container:

bash
Copy code
docker run --name university-db -e POSTGRES_USER=student -e POSTGRES_PASSWORD=student_pass -d -p 5432:5432 postgres
Start the Flask application container:

bash
Copy code
docker run --name flask-app -p 5000:5000 --link university-db flask-app
3. Manually Run Locally (Optional)
Create a virtual environment and activate it:

bash
Copy code
python -m venv venv
source venv/bin/activate  # For Linux/macOS
venv\Scripts\activate     # For Windows
Install dependencies:

bash
Copy code
pip install -r requirements.txt
Set up the database:

Use SQL_queries/ to create the StudentSchedule table and insert sample data.
Update app.py with your PostgreSQL connection details.
Run the Flask application:

bash
Copy code
python app.py
Open the application in your browser:

arduino
Copy code
http://127.0.0.1:5000
Endpoints
/: Homepage displaying a brief overview or navigation.
/timetable: Displays the student's schedule from the database.
