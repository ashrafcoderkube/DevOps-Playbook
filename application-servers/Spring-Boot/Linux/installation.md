# Spring Boot Installation Guide for Linux

## Prerequisites
- Java Development Kit (JDK) installed
- An active internet connection

## Step-by-Step Installation

### 1. Verify Java Installation
1. Open your Terminal.
2. Type the following command to check the Java version:
   ```sh
   java -version
   ```
   You should see the installed version of Java.

### 2. Install Spring Boot CLI (Optional)
1. Spring Boot CLI is a command-line tool that can be useful for quick prototyping.
2. To install Spring Boot CLI, download the tar.gz file from the official Spring website.
3. Extract the tar.gz file to a directory of your choice:
   ```sh
   tar -xvf spring-boot-cli-<version>.tar.gz -C /opt/
   ```
   Replace `<version>` with the appropriate version number.
4. Add the `bin` directory to your system's PATH environment variable by editing the `.bashrc` file:
   ```sh
   nano ~/.bashrc
   ```
   Add the following line at the end of the file:
   ```sh
   export PATH=$PATH:/opt/spring-boot-cli-<version>/bin
   ```
   Save the file and reload the bash profile:
   ```sh
   source ~/.bashrc
   ```

### 3. Install Spring Tool Suite (STS) (Optional)
1. Spring Tool Suite (STS) is an Eclipse-based IDE specifically designed for Spring development.
2. Download the STS tar.gz file from the official Spring website.
3. Extract the tar.gz file to a directory of your choice:
   ```sh
   tar -xvf sts-<version>.tar.gz -C /opt/
   ```
   Replace `<version>` with the appropriate version number.
4. Navigate to the STS directory and run the `STS` executable:
   ```sh
   cd /opt/sts-<version>/
   ./STS
   ```
5. Follow the prompts to set up your workspace.

### 4. Create a Spring Boot Project
1. Open your Terminal or STS.
2. To create a new Spring Boot project using the Spring Initializr, run the following command:
   ```sh
   spring init --name myproject --dependencies web
   ```
   Replace `myproject` with your desired project name.

### 5. Run the Spring Boot Application
1. Navigate to your project directory:
   ```sh
   cd myproject
   ```
2. Run the application with the following command:
   ```sh
   ./mvnw spring-boot:run
   ```
3. Open your web browser and go to `http://localhost:8080/` to see the Spring Boot welcome page.

## Conclusion
Congratulations! You have successfully installed Spring Boot on your Linux system. You can now start building and running Spring Boot applications.

### Additional Resources
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- [Spring Tool Suite Documentation](https://docs.spring.io/sts/docs/latest/reference/html/)
