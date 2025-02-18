# Flask Installation Guide for Windows

## Prerequisites
- Python installed on your system
- An active internet connection

## Step-by-Step Installation

### 1. Verify Python Installation
1. Open the Command Prompt by searching for `cmd` in the Start Menu and selecting `Command Prompt`.
2. Type the following command to check the Python version:
   ```sh
   python --version
   ```
   You should see the installed version of Python.

### 2. Upgrade pip (Python Package Installer)
1. Ensure pip is up to date by running the following command:
   ```sh
   python -m pip install --upgrade pip
   ```

### 3. Install Flask
1. In the Command Prompt, run the following command to install Flask:
   ```sh
   python -m pip install Flask
   ```

### 4. Verify Flask Installation
1. To verify the installation, type the following command:
   ```sh
   python -m flask --version
   ```
   You should see the installed version of Flask.

### 5. Create a Flask Project
1. Create a new directory for your project:
   ```sh
   mkdir myflaskapp
   cd myflaskapp
   ```
2. Create a new Python file called `app.py` and open it in a text editor.
3. Add the following code to `app.py`:
   ```python
   from flask import Flask

   app = Flask(__name__)

   @app.route('/')
   def hello_world():
       return 'Hello, World!'

   if __name__ == '__main__':
       app.run(debug=True)
   ```

### 6. Run the Flask Application
1. In the Command Prompt, navigate to your project directory:
   ```sh
   cd myflaskapp
   ```
2. Run the Flask application with the following command:
   ```sh
   python app.py
   ```
3. Open your web browser and go to `http://127.0.0.1:5000/` to see the "Hello, World!" message.

## Conclusion
Congratulations! You have successfully installed Flask on your Windows system. You can now start building and running Flask applications.

### Additional Resources
- [Flask Documentation](https://flask.palletsprojects.com/en/2.0.x/)

