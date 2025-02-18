# Spring Boot Installation Guide for macOS

## Prerequisites
- Java Development Kit (JDK) installed
- An active internet connection

## Step-by-Step Installation

### 1. Verify Java Installation
1. Open the Terminal application. You can find it in `Applications` > `Utilities` > `Terminal`.
2. Type the following command to check the Java version:
   ```sh
   java -version
   ```
   You should see the installed version of Java.

### 2. Install Homebrew (Optional but recommended)
1. Homebrew is a package manager for macOS that can simplify the installation process.
2. To install Homebrew, run the following command in the Terminal:
   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

### 3. Install Spring Boot CLI (Optional)
1. Spring Boot CLI is a command-line tool that can be useful for quick prototyping.
2. If you have Homebrew installed, run the following command to install Spring Boot CLI:
   ```sh
   brew tap spring-io/tap
   brew install spring-boot
   ```

### 4. Install Spring Tool Suite (STS) (Optional)
1. Spring Tool Suite (STS) is an Eclipse-based IDE specifically designed for Spring development.
2. Download the STS zip file from the official Spring website.
3. Extract the zip file to a directory of your choice.
4. Open the `STS.app` file to launch the IDE.
5. Follow the prompts to set up your workspace.

### 5. Create a Spring Boot Project
1. Open your Terminal or STS.
2. To create a new Spring Boot project using the Spring Initializr, run the following command:
   ```sh
   spring init --name myproject --dependencies web
   ```
   Replace `myproject` with your desired project name.

### 6. Run the Spring Boot Application
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
Congratulations! You have successfully installed Spring Boot on your macOS system. You can now start building and running Spring Boot applications.

### Additional Resources
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- [Spring Tool Suite Documentation](https://docs.spring.io/sts/docs/latest/reference/html/)

