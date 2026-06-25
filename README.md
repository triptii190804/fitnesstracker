🏋️ FitnessTracker — REST API Backend


A production-ready RESTful backend built with Java & Spring Boot to help users track workouts, monitor progress, and achieve fitness goals — designed with scalability, clean architecture, and developer-friendly APIs.



📌 What is FitnessTracker?

FitnessTracker is a backend API service that enables users to:


📝 Log workouts — record exercise type, duration, sets, reps, and calories burned
📊 Track progress — view historical workout data and monitor improvements over time
👤 Manage profiles — create and update personal fitness goals
🔐 Secure access — role-based access control ensuring data privacy


Built to demonstrate real-world backend engineering: clean REST API design, relational data modelling, input validation, and structured error handling.


🚀 Tech Stack

LayerTechnologyLanguageJava 17FrameworkSpring Boot 3.xDatabaseMySQL 8.0ORMSpring Data JPA / HibernateBuild ToolMavenAPI TestingPostmanVersion ControlGit / GitHub


🗂️ Project Structure

fitnesstracker/
├── src/
│   └── main/
│       └── java/
│           └── org/example/
│               ├── controller/       # REST API endpoints
│               ├── service/          # Business logic layer
│               ├── repository/       # Data access layer (JPA)
│               ├── model/            # Entity classes
│               └── dto/              # Request/Response DTOs
├── pom.xml
└── README.md


📡 API Endpoints

👤 User

MethodEndpointDescriptionPOST/api/users/registerRegister a new userGET/api/users/{id}Get user profilePUT/api/users/{id}Update fitness goals

🏋️ Workouts

MethodEndpointDescriptionPOST/api/workoutsLog a new workoutGET/api/workouts/{userId}Get all workouts for a userGET/api/workouts/{id}Get specific workout detailsPUT/api/workouts/{id}Update a workout entryDELETE/api/workouts/{id}Delete a workout entry

📊 Progress

MethodEndpointDescriptionGET/api/progress/{userId}Get progress summaryGET/api/progress/{userId}/weeklyGet weekly workout stats


🧱 Database Schema

sql-- Users table
CREATE TABLE users (
    id          BIGINT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(100) NOT NULL,
    email       VARCHAR(150) UNIQUE NOT NULL,
    goal        VARCHAR(255),
    created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Workouts table
CREATE TABLE workouts (
    id              BIGINT AUTO_INCREMENT PRIMARY KEY,
    user_id         BIGINT NOT NULL,
    exercise_name   VARCHAR(100) NOT NULL,
    duration_mins   INT NOT NULL,
    calories_burned INT,
    sets            INT,
    reps            INT,
    workout_date    DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);


⚙️ Getting Started

Prerequisites


Java 17+
MySQL 8.0+
Maven 3.8+


1. Clone the repository

bashgit clone https://github.com/triptii190804/fitnesstracker.git
cd fitnesstracker

2. Configure the database

Create a MySQL database:

sqlCREATE DATABASE fitnessdb;

Update src/main/resources/application.properties:

propertiesspring.datasource.url=jdbc:mysql://localhost:3306/fitnessdb
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

3. Build and run

bashmvn clean install
mvn spring-boot:run

The API will be available at: http://localhost:8080


🧪 Sample API Usage

Log a workout

bashcurl -X POST http://localhost:8080/api/workouts \
  -H "Content-Type: application/json" \
  -d '{
    "userId": 1,
    "exerciseName": "Running",
    "durationMins": 30,
    "caloriesBurned": 300,
    "sets": null,
    "reps": null,
    "workoutDate": "2026-06-26"
  }'

Get user progress

bashcurl http://localhost:8080/api/progress/1/weekly


✅ Key Features


Clean REST API design — proper HTTP methods, status codes, and response structures
Input Validation — @Valid annotations with meaningful error messages
Layered Architecture — Controller → Service → Repository separation of concerns
Relational Data Modelling — normalized schema with foreign key relationships
Error Handling — global exception handler with structured error responses
Scalable Design — stateless API design ready for horizontal scaling



🔮 Upcoming Features


 JWT Authentication & Authorization
 Docker containerization
 GitHub Actions CI/CD pipeline
 Progress analytics with charts data
 Exercise recommendation engine (AI-powered)
 Weekly email summary (notification service)



👩‍💻 Author

Tripti Singh


🔗 LinkedIn
📧 triptis512@gmail.com
🐙 GitHub



📄 License

This project is open source and available under the MIT License.
