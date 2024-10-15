
# Spring Security JWT Project

This project demonstrates how to implement **JWT (JSON Web Token) Authentication** with **Spring Security**. It includes features like user registration, login, token generation, and role-based access control using JWT tokens. The project uses a combination of Spring Boot, Spring Security, and JPA for authentication and authorization.

## Features

- User registration with encrypted passwords (BCrypt)
- JWT token generation for authentication
- Stateless session management using JWT
- User roles and authorities for restricted access
- Sample CRUD operations for students data

## Technologies Used

- Java 17
- Spring Boot 3.x
- Spring Security
- JWT (JSON Web Token)
- JPA/Hibernate
- MySQL Database
- Maven

## Project Structure

- `config`: Contains security configuration, JWT filter, and authentication provider setup.
- `controller`: REST API endpoints for handling requests.
  - `HelloController`: Greets users.
  - `StudentController`: Handles CRUD operations for students.
  - `UserController`: Manages user registration and login.
- `model`: Defines the entities (`Users`, `Student`) and UserDetails implementation.
- `repo`: JPA repository for interacting with the database.
- `service`: Handles business logic such as JWT token generation, user registration, and login.

## Getting Started

### Prerequisites

- JDK 17 or later
- Maven 3.x
- MySQL 8.x or later
- An IDE (e.g., IntelliJ IDEA, Eclipse, VS Code)
- Git

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/your-repository-name.git
   cd your-repository-name

2. **Set up the MySQL database:**
 - **Create a database in MySQL:**
    ```MySQL
    CREATE DATABASE spring_secur_ex;
 - **Update the database configuration in the ```application.properties``` file:**
    ```properties
    spring.datasource.url=jdbc:mysql://localhost:3306/spring_secur_ex
    spring.datasource.username=your-username
    spring.datasource.password=your-password
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
3. **Build the project using Maven:**
    ```bash
    mvn clean Install
4. **Run the application:**
    ```bash
    mvn spring-boot:run

### API Endpoints
- **User Registration:** ```POST /register```
   - **Payload:**
        ```json
        {
            "username": "your-username",
            "password": "your-password"
        }

    - **Response:** JWT token

- **Get All Students:** ```GET /students```
    - **Headers:** ```Authorization: Bearer <JWT_TOKEN>```

- **Add Student:** ```POST /students```
    - **Payload:**
        ```json
        {
            "id": 6,
            "name": "new-student",
            "mark": 85
        }

### Security Configuration
- JWT authentication is handled by ```JwtFilter```, which verifies the token and authenticates the user.
- Passwords are stored securely using **BCrypt** in the database.
- Roles and authorities are handled by ```UserPrincipal``` for user details and granted authorities.

### Sample Users
- You can create users using the ```/register``` endpoint or configure sample users in your database. Sample users include:

    Username: ```user```, Password: ```password``` (ROLE_USER)

    Username: ```admin```, Password: ```adminpass``` (ROLE_ADMIN)

### How JWT Works
- Login: Users send their credentials to ```/login```, and if the authentication is successful, the server generates a JWT.
- Request: For further requests, users must include the JWT in the ```Authorization``` header (```Bearer <JWT_TOKEN>```).
- Validation: The ```JwtFilter``` intercepts the request, validates the token, and sets the user’s authentication in the ```SecurityContext```.

### Database
The project uses MySQL for database management. You can configure the database connection settings in ```application.properties```.




