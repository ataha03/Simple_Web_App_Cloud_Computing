# Cloud Computing Project: Student Information Management System

This project demonstrates a containerised web application for managing student information, built using Flask for the frontend, FastAPI for the API, PostgreSQL for the database, and orchestrated with Docker Compose. This system allows users to add student records and view all existing records through a web interface, with Adminer providing a graphical interface for database management.

## Table of Contents
* [Features](#features)
* [Technologies Used](#technologies-used)
* [Project Structure](#project-structure)
* [Setup and Installation](#setup-and-installation)
  * [Prerequisites](#prerequisites)
  * [Running the Application with Docker Compose](#running-the-application-with-docker-compose)
* [Usage](#usage)
* [Screenshots](#screenshots)

## Features
* Web-App (Flask): A simple web interface for adding and viewing student information.
* API (FastAPI): A robust backend API for handling student data operations (add, retrieve).
* PostgreSQL Database: Persistent storage for student records.
* Adminer: A web-based database management tool for easy interaction with the PostgreSQL database.
* Dockerisation: All components (web-app, API, database, Adminer) are containerised using Docker.
* Docker Compose: Unified orchestration for all services, simplifying deployment and management.
* Network Segmentation: Utilises separate frontend and backend networks for secure and organised inter-service communication.
* Data Persistence: Uses Docker volumes to ensure database data persists across container restarts.

## Technologies Used
* Python 3.9: Programming language for Flask and FastAPI applications.
* Flask: Web framework for the frontend application.
* FastAPI: Modern, fast (high-performance) web framework for building APIs.
* PostgreSQL: Open-source relational database.
* Adminer: Database management tool.
* Docker: Containerisation platform.
* Docker Compose: Tool for defining and running multi-container Docker applications.
* Uvicorn: ASGI server for running FastAPI applications.
* SQLAlchemy: Python SQL toolkit and Object Relational Mapper (ORM).

## Project Structure
The project is organised into several directories, each containing a Dockerfile and relevant source code for its service.

├── api

│---└── api

│------├── Dockerfile

│------├── main.py

│------├── db_setup.py

│------└── requirements.txt

├── web-app

│---└── web-app

│------├── Dockerfile

│------├── app.py

│------├── requirements.txt

│------└── templates

│--------- └── students.html

├── docker-compose.yaml

└── .env

## Setup and Installation
### Prerequisites
Before you begin, ensure you have the following installed on your system:
* Docker Desktop (includes Docker Engine and Docker Compose)

### Running the Application with Docker Compose
The easiest way to get the entire application running is by using Docker Compose.
1. Clone the repository:
```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
```

2. Create a .env file:
In the root directory of your project (same level as docker-compose.yaml), create a file named .env and add your PostgreSQL credentials:
```bash
POSTGRES_DB=student
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
```

3. Build and run the services:
Navigate to the root directory of the project in your terminal and run:
```bash
docker compose up --build -d
```

This command will:
* Build the web-app and api Docker images.
* Start all services (database, adminer, web-app, api) in detached mode (-d).
* Create the necessary frontend and backend networks, and the db_data volume.

4. Verify services:
You can check the status of your running containers with:
```bash
docker ps
```

5. Access the applications:
* Web-App: Access the Flask web application at http://localhost:8090/add (to add students) and http://localhost:8090/all (to view all students).
* FastAPI Docs: View the FastAPI interactive documentation (Swagger UI) at http://localhost:8080/docs.
* Adminer: Access the Adminer database management interface at http://localhost:8091.
  * System: PostgreSQL
  * Server: database
  * Username: postgres
  * Password: password
  * Database: student
  
## Usage
### Adding Student Information
Navigate to http://localhost:8090/add in your web browser.
Fill in the student details (Student ID, First Name, Last Name, Module Code).
Click "Submit" to add the student to the database.

### Viewing Student Information
Navigate to http://localhost:8090/all to see a table of all students currently in the database.

### Managing Database with Adminer
Navigate to http://localhost:8091 and log in using the credentials provided in the "Setup and Installation" section.
You can browse tables, view data, and perform various database operations through the Adminer interface.

## Screenshots
Web-App - Student Information Form (Empty)
![image](https://github.com/user-attachments/assets/5ffde079-5e4c-4ddd-9b25-970c93b40235)

Web-App - Student Information Form (Filled)
![image](https://github.com/user-attachments/assets/529e33b0-c4cc-4663-bf1a-21d551ed552d)

Web-App - All Students View
![image](https://github.com/user-attachments/assets/1d656f50-6f66-4d22-aa80-61768078a217)

FastAPI Docs (Swagger UI)
![image](https://github.com/user-attachments/assets/7efc4e65-51ae-4984-b544-c9c6c9c0485c)

Adminer Login Page
![image](https://github.com/user-attachments/assets/e3dd3c9f-040f-4a4f-afaa-8151e1d41765)

Adminer Database View with Student Table
![image](https://github.com/user-attachments/assets/b45c7d7b-50bb-400f-847e-2e0ace33a88d)
