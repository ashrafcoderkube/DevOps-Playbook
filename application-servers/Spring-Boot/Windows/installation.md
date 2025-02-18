# Spring Boot Installation Guide for Windows

## Prerequisites
- Java Development Kit (JDK) installed
- An active internet connection

## Step-by-Step Installation

### 1. Verify Java Installation
1. Open the Command Prompt by searching for `cmd` in the Start Menu and selecting `Command Prompt`.
2. Type the following command to check the Java version:
   ```sh
   java -version
   ```
   You should see the installed version of Java.

### 2. Install Spring Boot CLI (Optional)
1. Spring Boot CLI is a command-line tool that can be useful for quick prototyping.
2. To install Spring Boot CLI, download the zip file from the official Spring website.
3. Extract the zip file to a directory of your choice.
4. Add the `bin` directory to your system's PATH environment variable.

### 3. Install Spring Tool Suite (STS) (Optional)
1. Spring Tool Suite (STS) is an Eclipse-based IDE specifically designed for Spring development on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).
2. Download the STS zip file from the official Spring website on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).
3. Extract the zip file to a directory of your choice on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).
4. Open the `STS.exe` file to launch the IDE on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).
5. Follow the prompts to set up your workspace on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).

### 4. Create a Spring Boot Project
1. Open your Command Prompt or STS on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).
2. To create a new Spring Boot project using the Spring Initializr, run the following command:
   ```sh
   spring init --name myproject --dependencies web
   ```
   Replace `myproject` with your desired project name on Windows 11 - Java Guides](https://www.javaguides.net/2024/11/how-to-install-spring-tool-suite-4-sts-on-windows-11.html).

### 5. Run the Spring Boot Application
1. Navigate to your project directory:
   ```sh
   cd myproject
   ```
2. Run the application with the following command:
   ```sh
   java -jar target/myproject-0.0.1-SNAPSHOT.jar
   ```
3. Open your web browser and go to `http://localhost:8080/` to see the Spring Boot welcome page.

## Conclusion
Congratulations! You have successfully installed Spring Boot on your Windows system. You can now start building and running Spring Boot applications.

### Additional Resources
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- [Spring Tool Suite Documentation](https://docs.spring.io/sts/docs/latest/reference/html/)
