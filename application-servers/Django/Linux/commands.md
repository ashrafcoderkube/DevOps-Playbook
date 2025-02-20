## Django Commands

### Project Commands
- **Create a new Django project:**
  ```sh
  django-admin startproject projectname
  ```
  Replace `projectname` with the name of your project.

### App Commands
- **Create a new Django app:**
  ```sh
  python manage.py startapp appname
  ```
  Replace `appname` with the name of your app.

### Development Server
- **Run the development server:**
  ```sh
  python manage.py runserver
  ```
- **Run the development server on a specific port:**
  ```sh
  python manage.py runserver 8080
  ```
  Replace `8080` with your desired port number.

### Database Commands
- **Make migrations for database changes:**
  ```sh
  python manage.py makemigrations
  ```
- **Apply database migrations:**
  ```sh
  python manage.py migrate
  ```

### User Management
- **Create a superuser:**
  ```sh
  python manage.py createsuperuser
  ```
  Follow the prompts to create a superuser account.

### Shell and Utility Commands
- **Open the Django shell:**
  ```sh
  python manage.py shell
  ```
- **Collect static files:**
  ```sh
  python manage.py collectstatic
  ```
- **Check for problems in the project without making changes:**
  ```sh
  python manage.py check
  ```

### Testing
- **Run tests:**
  ```sh
  python manage.py test
  ```

### Internationalization
- **Compile message files:**
  ```sh
  python manage.py compilemessages
  ```
- **Create message files:**
  ```sh
  python manage.py makemessages -l <language-code>
  ```
  Replace `<language-code>` with the appropriate language code (e.g., `en` for English).

These commands can be executed in the terminal or command prompt, regardless of the operating system you are using. The syntax and usage remain consistent across Windows, macOS, Linux, and Ubuntu.
