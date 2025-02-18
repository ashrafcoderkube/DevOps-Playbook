# Ruby on Rails Installation Guide for Windows

## Prerequisites
- Windows 10 or Windows 11 (version 2004 and higher)
- An active internet connection

## Step-by-Step Installation

### 1. Install Windows Subsystem for Linux (WSL)
1. Open PowerShell as an Administrator and run the following command:
   ```sh
   wsl --install --distribution Ubuntu-24.04
   ```
2. Reboot your computer to complete the installation.

### 2. Set Up Ubuntu
1. After rebooting, open Ubuntu from the Start Menu.
2. Create a new user account by following the prompts and set a username and password.

### 3. Install Dependencies
1. Open the Ubuntu terminal and run the following commands to install dependencies:
   ```sh
   sudo apt update
   sudo apt install build-essential rustc libssl-dev libyaml-dev zlib1g-dev libgmp-dev
   ```

### 4. Install Ruby Version Manager (Mise)
1. Install Mise by running the following command:
   ```sh
   curl https://mise.run | sh
   ```
2. Add Mise to your shell configuration:
   ```sh
   echo 'eval "$(~/.local/bin/mise activate)"' >> ~/.bashrc
   source ~/.bashrc
   ```

### 5. Install Ruby
1. Install Ruby using Mise:
   ```sh
   mise use --global ruby@3
   ```
2. Verify the installation:
   ```sh
   ruby --version
   ```

### 6. Install Rails
1. Install Rails using the following command:
   ```sh
   gem install rails
   ```
2. Verify the installation:
   ```sh
   rails --version
   ```

### 7. Set Up Git
1. Install Git if it's not already installed:
   ```sh
   sudo apt install git
   ```
2. Configure Git with your username and email:
   ```sh
   git config --global user.name "YOUR NAME"
   git config --global user.email "YOUR@EMAIL.com"
   ```

### 8. Create a New Rails Project
1. Create a new Rails project:
   ```sh
   rails new myrailsapp
   cd myrailsapp
   ```

### 9. Run the Rails Server
1. Start the Rails server:
   ```sh
   rails server
   ```
2. Open your web browser and go to `http://localhost:3000` to see the Rails welcome page.

## Conclusion
Congratulations! You have successfully installed Ruby on Rails on your Windows system. You can now start building and running Rails applications.

### Additional Resources
- [Ruby on Rails Guides](https://guides.rubyonrails.org/install_ruby_on_rails.html)
- [GoRails Setup Guide](https://gorails.com/setup/windows/10)

