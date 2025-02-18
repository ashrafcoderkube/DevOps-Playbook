## Spring Boot Commands (Ubuntu)

### Project Creation
- **Create a new Spring Boot project:**
  ```sh
  spring init --name projectname --dependencies web
  ```
  Replace `projectname` with your desired project name.

### Maven Commands
- **Build the project using Maven:**
  ```sh
  mvn clean install
  ```
- **Run the application using Maven:**
  ```sh
  mvn spring-boot:run
  ```
- **Run tests:**
  ```sh
  mvn test
  ```

### Gradle Commands
- **Build the project using Gradle:**
  ```sh
  ./gradlew build
  ```
- **Run the application using Gradle:**
  ```sh
  ./gradlew bootRun
  ```
- **Run tests:**
  ```sh
  ./gradlew test
  ```

### Spring Boot CLI Commands (if installed)
- **Run a Spring Boot application from a Groovy script:**
  ```sh
  spring run app.groovy
  ```
- **List the Spring Boot versions available for use:**
  ```sh
  spring boot --list-versions
  ```
- **Install a specific Spring Boot version:**
  ```sh
  spring boot install <version>
  ```
  Replace `<version>` with the desired version number.

### Other Useful Commands
- **Check Spring Boot version:**
  ```sh
  mvn dependency:tree | grep spring-boot
  ```
- **Generate a Docker image for the application:**
  ```sh
  ./mvnw spring-boot:build-image
  ```

These commands can be used in the Terminal on Ubuntu to manage your Spring Boot projects.