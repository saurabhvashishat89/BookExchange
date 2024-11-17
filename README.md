Book Exchange Platform
A Spring Boot application that enables users to securely register, list, search, and exchange books. The platform uses MySQL for the database and JWT for authentication.

Features
User Management:

Secure user registration and login using JWT.
Password encryption with BCryptPasswordEncoder.
Password recovery and logout functionality.
Book Listings:

Users can add, update, delete, and view their book listings.
Book attributes include title, author, genre, condition, and availability status.
Book Search:

Search books by title, author, genre, and location.
Filter search results by availability, genre, and location.
Paginated search results.
Authentication:

Token-based authentication using JWT.
CSRF protection configured to exclude public endpoints.
Technologies Used
Backend: Spring Boot, Spring Security, Hibernate, JPA.
Database: MySQL.
Authentication: JSON Web Tokens (JWT).
Validation: Hibernate Validator.
Logging: Logback.
Build Tool: Maven.
Installation
Prerequisites
Java 17 (OpenJDK 17 or Oracle JDK 17).
MySQL Server.
Maven.
Steps
Clone the Repository:

bash
Copy code
git clone https://github.com/saurabhvashishat89/BookExchange.git
cd bookexchange
Configure the Database:

Update the application.properties file with your MySQL configuration:
properties
Copy code
spring.datasource.url=jdbc:mysql://localhost:3306/bookexchange
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>
spring.jpa.hibernate.ddl-auto=update
Run the Application:

bash
Copy code
mvn spring-boot:run
Access the Application:

API Base URL: http://localhost:8080.
Endpoints
User Management
HTTP Method	Endpoint	Description
POST	/api/users/register	Register a new user
POST	/api/users/login	Authenticate and get a JWT token
POST	/api/users/logout	Logout the user
Book Listings
HTTP Method	Endpoint	Description
POST	/api/books	Add a new book listing
GET	/api/books/{id}	View book details
PUT	/api/books/{id}	Update a book listing
DELETE	/api/books/{id}	Delete a book listing
Book Search
HTTP Method	Endpoint	Description
GET	/api/books/search	Search books with filters
Testing the APIs
Register User
bash
Copy code
curl -X POST "http://localhost:8080/api/users/register" \
-H "Content-Type: application/json" \
-d '{"email":"user@example.com","password":"password123"}'
Login User
bash
Copy code
curl -X POST "http://localhost:8080/api/users/login" \
-H "Content-Type: application/json" \
-H "email:user@example.com" \
-H "password:password123" \

Add Book
bash
Copy code
curl -X POST "http://localhost:8080/api/books" \
-H "Authorization: Bearer <JWT_TOKEN>" \
-H "Content-Type: application/json" \
-d '{"title":"Book Title","author":"Author Name","genre":"Fiction","condition":"New","availabilityStatus":"Available"}'
Key Configurations
Logback
The application uses Logback for logging. Logs are configured in the logback.xml file located in the src/main/resources directory.

com/your-repository/bookexchange