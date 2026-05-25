# 📋 Task Manager API

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
    <img src="https://img.shields.io/badge/Spring_Boot-3.2-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white"/>
      <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
        <img src="https://img.shields.io/badge/Docker-ready-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
          <img src="https://img.shields.io/badge/JWT-Auth-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white"/>
            <img src="https://img.shields.io/badge/Swagger-UI-85EA2D?style=for-the-badge&logo=swagger&logoColor=black"/>
</p>p>

<p align="center">
  A production-ready RESTful Task Management API built with <strong>Spring Boot 3.2</strong>strong>, featuring JWT authentication, role-based access control, and full CRUD operations.
</p>p>

---

## 🚀 Features

- **JWT Authentication & Authorization** — Stateless security with access/refresh tokens
- - **Role-Based Access Control** — `ADMIN` and `USER` roles with Spring Security
  - - **Full CRUD for Tasks** — Create, read, update, delete tasks with priority/status filters
    - - **Pagination & Sorting** — Efficient data retrieval with Spring Data JPA
      - - **Global Exception Handling** — Consistent error responses using `@ControllerAdvice`
        - - **API Documentation** — Interactive Swagger UI at `/swagger-ui.html`
          - - **Dockerized** — Ready-to-run with Docker Compose (app + MySQL)
            - - **Unit & Integration Tests** — JUnit 5 + Mockito + Testcontainers
              -
              - ---
              -
              - ## 🛠️ Tech Stack
              -
              - | Layer | Technology |
              - |-------|-----------|
              - | Language | Java 17 |
              - | Framework | Spring Boot 3.2 |
              - | Security | Spring Security + JWT (jjwt) |
              - | Database | MySQL 8.0 |
              - | ORM | Spring Data JPA / Hibernate |
              - | Build | Maven |
              - | Containerization | Docker + Docker Compose |
              - | API Docs | SpringDoc OpenAPI (Swagger UI) |
              - | Testing | JUnit 5, Mockito, Testcontainers |
              -
              - ---
              -
              - ## 📁 Project Structure
              -
              - ```
                task-manager-api/
                ├── src/main/java/com/vijay/taskmanager/
                │   ├── config/          # Security, JWT, Swagger config
                │   ├── controller/      # REST controllers
                │   ├── dto/             # Request/Response DTOs
                │   ├── entity/          # JPA entities (User, Task)
                │   ├── exception/       # Custom exceptions & global handler
                │   ├── repository/      # Spring Data JPA repositories
                │   ├── security/        # JWT filter, UserDetailsService
                │   └── service/         # Business logic layer
                ├── src/test/            # Unit and integration tests
                ├── docker-compose.yml
                └── pom.xml
                ```

                ---

                ## 🔌 API Endpoints

                ### Auth
                | Method | Endpoint | Description |
                |--------|----------|-------------|
                | POST | `/api/auth/register` | Register new user |
                | POST | `/api/auth/login` | Login & get JWT token |
                | POST | `/api/auth/refresh` | Refresh access token |

                ### Tasks
                | Method | Endpoint | Description |
                |--------|----------|-------------|
                | GET | `/api/tasks` | Get all tasks (paginated) |
                | GET | `/api/tasks/{id}` | Get task by ID |
                | POST | `/api/tasks` | Create new task |
                | PUT | `/api/tasks/{id}` | Update task |
                | DELETE | `/api/tasks/{id}` | Delete task |
                | GET | `/api/tasks/status/{status}` | Filter by status |
                | GET | `/api/tasks/priority/{priority}` | Filter by priority |

                ---

                ## ⚙️ Getting Started

                ### Prerequisites
                - Java 17+
                - - Maven 3.8+
                  - - Docker & Docker Compose (optional)
                    -
                    - ### Run with Docker Compose
                    -
                    - ```bash
                      git clone https://github.com/VijayKatupilla/task-manager-api.git
                      cd task-manager-api
                      docker-compose up --build
                      ```

                      App will be available at `http://localhost:8080`
                      Swagger UI: `http://localhost:8080/swagger-ui.html`

                      ### Run Locally

                      ```bash
                      # Clone the repository
                      git clone https://github.com/VijayKatupilla/task-manager-api.git
                      cd task-manager-api

                      # Configure DB in application.properties
                      spring.datasource.url=jdbc:mysql://localhost:3306/taskdb
                      spring.datasource.username=root
                      spring.datasource.password=yourpassword

                      # Build and run
                      mvn clean install
                      mvn spring-boot:run
                      ```

                      ---

                      ## 🧪 Sample Request

                      ```bash
                      # Register
                      curl -X POST http://localhost:8080/api/auth/register \
                        -H "Content-Type: application/json" \
                        -d '{"username":"vijay","email":"vijay@example.com","password":"Pass@123"}'

                      # Create a Task (with JWT token)
                      curl -X POST http://localhost:8080/api/tasks \
                        -H "Authorization: Bearer <your-token>" \
                        -H "Content-Type: application/json" \
                        -d '{"title":"Fix login bug","priority":"HIGH","status":"TODO","dueDate":"2026-06-30"}'
                      ```

                      ---

                      ## 📊 Task Entity

                      ```java
                      @Entity
                      public class Task {
                          private Long id;
                          private String title;
                          private String description;
                          private Priority priority;   // HIGH, MEDIUM, LOW
                          private Status status;       // TODO, IN_PROGRESS, DONE
                          private LocalDate dueDate;
                          private LocalDateTime createdAt;
                          // ManyToOne -> User
                      }
                      ```

                      ---

                      ## 📄 License

                      This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

                      ---

                      <p align="center">Made with ❤️ by <a href="https://github.com/VijayKatupilla">Vijay Sai Kumar</a>a></p>p></strong>
