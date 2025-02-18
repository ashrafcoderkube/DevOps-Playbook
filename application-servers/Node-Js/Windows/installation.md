# Node.js Installation Guide for Windows

## Prerequisites
- Administrator privileges
- An active internet connection

## Step-by-Step Installation

### 1. Download Node.js Installer
1. Open your web browser and go to the official [Node.js download page](https://nodejs.org/en/download/).
2. Download the Windows Installer (.msi) for the LTS version.

### 2. Run the Installer
1. Locate the downloaded `.msi` file and double-click to run the installer.
2. You might see a User Account Control prompt asking for permission to allow the program to make changes to your computer. Click `Yes`.

### 3. Follow the Setup Wizard
1. The Node.js Setup Wizard will open. Click `Next`.
2. Accept the License Agreement and click `Next`.
3. Choose the installation location (default is recommended) and click `Next`.
4. Select the components you want to install. By default, all components are selected. Click `Next`.
5. Click `Install` to begin the installation.
6. Once the installation is complete, click `Finish` to close the Setup Wizard.

### 4. Verify Installation
1. Open the Command Prompt by searching for `cmd` in the Start Menu and selecting `Command Prompt`.
2. Type the following command to check the Node.js version:
   ```sh
   node -v
   ```
   You should see the installed version of Node.js.
3. Next, check the npm (Node Package Manager) version:
   ```sh
   npm -v
   ```
   You should see the installed version of npm.

### 5. Update Environment Variables (if needed)
1. If you face issues with running `node` or `npm` commands, you might need to manually set the PATH variable.
2. Go to `Control Panel` > `System and Security` > `System` > `Advanced system settings`.
3. Click on `Environment Variables`.
4. In the `System variables` section, find the `Path` variable and click `Edit`.
5. Add the path to the Node.js installation (e.g., `C:\Program Files\nodejs\`) and click `OK`.
6. Restart your Command Prompt.

## Conclusion
Congratulations! You have successfully installed Node.js on your Windows system. You can now start building and running Node.js applications.

### Additional Resources
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [npm Documentation](https://docs.npmjs.com/)
