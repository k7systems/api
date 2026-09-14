# K7 Systems API

`k7systems-api` is the backend REST API for K7 Systems. It is currently in early
development and exposes a minimal Spring Boot application with a health/status
endpoint. Future functionality will be added incrementally as the project grows.

## Technologies Used

- Java 25
- Spring Boot 4.1.1 (Spring Web)
- Maven (via the included Maven Wrapper)
- JUnit 5 / Spring Boot Test (MockMvc)

## Requirements

- JDK 25
- No local Maven installation is required — this project uses the Maven
  Wrapper (`mvnw` / `mvnw.cmd`), which downloads the correct Maven version
  automatically.

## Running Locally

From the project root:

```bash
# macOS / Linux
./mvnw spring-boot:run

# Windows
mvnw.cmd spring-boot:run
```

The application starts on `http://localhost:8080` by default.

## Building with Maven

```bash
# macOS / Linux
./mvnw clean package

# Windows
mvnw.cmd clean package
```

This produces an executable JAR in the `target/` directory, which can be run with:

```bash
java -jar target/k7systems-api-0.0.1-SNAPSHOT.jar
```

## Example API Request

```
GET http://localhost:8080/api/health
```

```bash
curl http://localhost:8080/api/health
```

## Example API Response

```json
{
  "status": "ok",
  "service": "k7systems-api"
}
```

## Project Structure

```
k7systems-api
├── src
│   ├── main
│   │   ├── java/com/k7systems/api
│   │   │   ├── K7systemsApiApplication.java   # application entry point
│   │   │   ├── controller
│   │   │   │   └── HealthController.java      # GET /api/health
│   │   │   └── model
│   │   │       └── HealthResponse.java        # response record
│   │   └── resources
│   │       └── application.properties
│   └── test
│       └── java/com/k7systems/api
│           ├── K7systemsApiApplicationTests.java
│           └── controller/HealthControllerTest.java
├── .github/workflows/build.yml                # CI: build + test on push/PR
├── pom.xml
└── README.md
```

Additional packages such as `service` and `config` will be added once there is
actual business logic or configuration to put in them.

## Roadmap

This project is intentionally minimal right now. Planned, not-yet-implemented
next steps include:

- Additional REST endpoints beyond `/api/health`
- A service layer for business logic
- Persistence / database integration
- Authentication and authorization
- Containerization (Docker)

None of the items above exist yet — they are listed here only as direction for
future work.
