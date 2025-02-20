# Node.js Installation Guide for Linux

## Prerequisites
- Administrator privileges
- An active internet connection

## Step-by-Step Installation

### 1. Update Package Index
1. Open your Terminal.
2. Update your package index by running the following command:
   ```sh
   sudo apt update
   ```

### 2. Install Node.js
1. You can install Node.js from the official repository. Run the following command:
   ```sh
   sudo apt install nodejs
   ```
2. Next, install npm (Node Package Manager):
   ```sh
   sudo apt install npm
   ```

### 3. Verify Installation
1. Once the installation is complete, verify the Node.js version:
   ```sh
   node -v
   ```
   You should see the installed version of Node.js.
2. Next, check the npm version:
   ```sh
   npm -v
   ```
   You should see the installed version of npm.

### 4. Install Node.js via NodeSource (Alternative Method)
1. You can also install a specific version of Node.js using NodeSource. First, add the NodeSource PPA (Personal Package Archive):
   ```sh
   curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
   ```
   Replace `14.x` with your desired Node.js version.
2. Install Node.js from NodeSource:
   ```sh
   sudo apt install nodejs
   ```

### 5. Update Environment Variables (if needed)
1. If you face issues with running `node` or `npm` commands, you might need to set the PATH variable manually.
2. Open your Terminal and enter the following command to open the `.bashrc` file in a text editor:
   ```sh
   nano ~/.bashrc
   ```
3. Add the following line to the file:
   ```sh
   export PATH="/usr/local/bin:$PATH"
   ```
4. Save the file by pressing `Ctrl + X`, then `Y`, and then `Enter`.
5. Apply the changes by running the following command:
   ```sh
   source ~/.bashrc
   ```

## Conclusion
Congratulations! You have successfully installed Node.js on your Linux system. You can now start building and running Node.js applications.

### Additional Resources
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [npm Documentation](https://docs.npmjs.com/)

