## Flask Commands (Windows)

### Project Setup
- **Create a new Flask project:**
  ```sh
  mkdir myflaskapp
  cd myflaskapp
  ```

### Virtual Environment
- **Create a virtual environment:**
  ```sh
  python -m venv venv
  ```
- **Activate the virtual environment:**
  ```sh
  venv\Scripts\activate
  ```

### Package Management
- **Install Flask within the virtual environment:**
  ```sh
  python -m pip install Flask
  ```

### Running the Application
- **Run the Flask application:**
  ```sh
  python app.py
  ```
  Or, if you use the Flask command line:
  ```sh
  flask run
  ```

### Flask Commands
- **Run the Flask application in debug mode:**
  ```sh
  flask run --debug
  ```
- **Specify the host and port:**
  ```sh
  flask run --host=0.0.0.0 --port=5000
  ```

### Database Migration (using Flask-Migrate)
- **Initialize the migration directory:**
  ```sh
  flask db init
  ```
- **Generate a new migration:**
  ```sh
  flask db migrate -m "description of migration"
  ```
- **Apply the migration:**
  ```sh
  flask db upgrade
  ```

### Environment Variables
- **Set the Flask application:**
  ```sh
  set FLASK_APP=app.py
  ```
- **Set the environment to development:**
  ```sh
  set FLASK_ENV=development
  ```

These commands will help you manage your Flask projects on Windows.