# issue-management-system
A full-stack Issue Management System built with Spring Boot and Angular.  It allows users to create, update, delete, and track issues with priority, status, and assignee details. Includes REST APIs, database integration, filtering, and validation.


##Configure Database(Application.properties)
spring.datasource.url=jdbc:mysql://localhost:3306/issue_db
spring.datasource.username=root
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
server.port=8080

#create MySQL database
CREATE DATABASE issue_db;

##Install Dependencies
Make sure you have:
Java 17+
Maven
MySQL

##Run the application
mvn spring-boot:run
http://localhost:8080  for backend
http://localhost:4200   for frontend


##Technologies Used
Java 17
Spring Boot
Spring Data JPA
Hibernate
MySQL
Maven
Angular (Frontend)
Postman (API Testing)


### API Endpoint
User APIs:
base url: http://localhost:8080/user

| Method | Endpoint | Description          |
| ------ | -------- | -------------------- |
| POST   | /signUp  | Register new user    |
| POST   | /login   | Login user           |


sign Up:
{
  "name": "John",
  "email": "john@example.com",
  "password": "1234",
  "role": "MANAGER"
}


Login:
{
  "email": "john@example.com",
  "password": "1234"
}



Issue API :
base url: http://localhost:8080/issue

| Method | Endpoint                                        | Description                  |
| ------ | ----------------------------------------------- | ---------------------------- |
| POST   | /add?userId={id}                                | Create new issue             |
| GET    | /viewUserIssue?userId={id}                      | View user's own issues       |
| GET    | /view?userId={id}                               | View all issues (role-based) |
| GET    | /filterStatus?status={STATUS}&userId={id}       | Filter by status             |
| GET    | /filterPriority?priority={PRIORITY}&userId={id} | Filter by priority           |
| PUT    | /updateDetails?issueId={id}&userId={id}         | Update issue details         |
| PUT    | /updateStatus?issueId={id}&userId={id}          | Update issue status          |
| POST   | /assign                                         | Assign issue to solver       |
| GET    | /solverIssue?assignee=email                      | Get issues by solver         |
| DELETE | /delete?issueId={id}&userId={id}                | Delete issue                 |


Add Issue:

{
  "title": "Login Bug",
  "description": "User cannot login",
  "priority": "HIGH"
}

Postman Tests:
POST /signUp → 201 Created
POST /login → 200 OK
POST /issue/add → 200 OK
PUT /issue/updateStatus → 200 OK
POST /issue/assign → 200 OK
DELETE /issue/delete → 200 OK
Error response → 400 / 405 / 404
