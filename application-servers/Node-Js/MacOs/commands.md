## Node.js Commands

### Basic Commands
- **Check Node.js version:**
  ```sh
  node -v
  ```
- **Execute a Node.js file:**
  ```sh
  node filename.js
  ```

### REPL (Read-Eval-Print Loop)
- **Start Node.js REPL:**
  ```sh
  node
  ```
- **Exit Node.js REPL:**
  ```sh
  .exit
  ```

### Package Management
- **Initialize a new Node.js project (create package.json):**
  ```sh
  npm init
  ```

## npm Commands

### Basic Commands
- **Check npm version:**
  ```sh
  npm -v
  ```
- **Install a package globally:**
  ```sh
  npm install -g package-name
  ```
- **Install a package locally:**
  ```sh
  npm install package-name
  ```
- **Install dependencies listed in package.json:**
  ```sh
  npm install
  ```
- **Update a package:**
  ```sh
  npm update package-name
  ```
- **Uninstall a package:**
  ```sh
  npm uninstall package-name
  ```

### Package Management
- **List globally installed packages:**
  ```sh
  npm list -g --depth=0
  ```
- **List locally installed packages:**
  ```sh
  npm list --depth=0
  ```

### Package Publishing
- **Login to npm registry:**
  ```sh
  npm login
  ```
- **Publish a package:**
  ```sh
  npm publish
  ```
- **Unpublish a package:**
  ```sh
  npm unpublish package-name
  ```

### Run Scripts
- **Run a script defined in package.json:**
  ```sh
  npm run script-name
  ```

These are some of the essential commands for Node.js and npm that you'll frequently use. You can use them on any operating system, including Windows, macOS, and Linux.