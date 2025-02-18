# Node.js Installation Guide for macOS

## Prerequisites
- Administrator privileges
- An active internet connection

## Step-by-Step Installation

### 1. Download Node.js Installer
1. Open your web browser and go to the official [Node.js download page](https://nodejs.org/en/download/).
2. Download the macOS Installer (.pkg) for the LTS version.

### 2. Run the Installer
1. Locate the downloaded `.pkg` file and double-click to run the installer.
2. The Installer will guide you through the installation process. Click `Continue` when prompted.

### 3. Follow the Setup Wizard
1. Read the license agreement and click `Continue`, then click `Agree` to accept the terms.
2. Choose the installation location (default is recommended) and click `Install`.
3. You might be prompted to enter your administrator password. Enter it and click `Install Software`.
4. Once the installation is complete, click `Close` to exit the Installer.

### 4. Verify Installation
1. Open the Terminal application. You can find it in `Applications` > `Utilities` > `Terminal`.
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
1. If you face issues with running `node` or `npm` commands, you might need to set the PATH variable manually.
2. Open the Terminal and enter the following command to open the `.bash_profile` file in a text editor:
   ```sh
   nano ~/.bash_profile
   ```
3. Add the following line to the file:
   ```sh
   export PATH="/usr/local/bin:$PATH"
   ```
4. Save the file by pressing `Ctrl + X`, then `Y`, and then `Enter`.
5. Apply the changes by running the following command:
   ```sh
   source ~/.bash_profile
   ```

## Conclusion
Congratulations! You have successfully installed Node.js on your macOS system. You can now start building and running Node.js applications.

### Additional Resources
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [npm Documentation](https://docs.npmjs.com/)
