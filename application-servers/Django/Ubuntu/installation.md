# Django Installation Guide for Ubuntu

## Prerequisites
- Python installed on your system
- An active internet connection

## Step-by-Step Installation

### 1. Verify Python Installation
1. Open your Terminal.
2. Type the following command to check the Python version:
   ```sh
   python3 --version
   ```
   You should see the installed version of Python.

### 2. Upgrade pip (Python Package Installer)
1. Ensure pip is up to date by running the following command:
   ```sh
   python3 -m pip install --upgrade pip
   ```

### 3. Install Django
1. In the Terminal, run the following command to install Django:
   ```sh
   python3 -m pip install Django
   ```
   This will download and install the latest Django release.

### 4. Verify Django Installation
1. To verify the installation, type the following command:
   ```sh
   django-admin --version
   ```
   You should see the installed version of Django.

### 5. Create a Django Project
1. To create a new Django project, run the following command:
   ```sh
   django-admin startproject projectname
   ```
   Replace `projectname` with the name of your project.

### 6. Run the Development Server
1. Navigate to your project directory:
   ```sh
   cd projectname
   ```
2. Run the development server with the following command:
   ```sh
   python3 manage.py runserver
   ```
3. Open your web browser and go to `http://127.0.0.1:8000/` to see the Django welcome page.

## Conclusion
Congratulations! You have successfully installed Django on your Ubuntu system. You can now start building and running Django projects.

### Additional Resources
- [Django Documentation](https://docs.djangoproject.com/en/5.1/)
- [Django on Ubuntu Guide](https://docs.djangoproject.com/en/5.1/howto/ubuntu/)