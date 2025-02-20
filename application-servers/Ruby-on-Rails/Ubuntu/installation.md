# Ruby on Rails Installation Guide for Ubuntu

## Prerequisites
- Ubuntu operating system (20.04 or higher)
- An active internet connection

## Step-by-Step Installation

### 1. Update Package Index
1. Open your Terminal.
2. Update your package index by running the following command:
   ```sh
   sudo apt update
   ```

### 2. Install Dependencies
1. Install necessary dependencies by running the following commands:
   ```sh
   sudo apt install curl gnupg build-essential libssl-dev libyaml-dev libsqlite3-dev sqlite3 zlib1g-dev
   sudo apt install libgmp-dev libreadline-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev
   ```

### 3. Install Ruby Version Manager (Mise)
1. Install Mise by running the following command:
   ```sh
   curl https://mise.run | sh
   ```
2. Add Mise to your shell configuration:
   ```sh
   echo 'eval "$(~/.local/bin/mise activate)"' >> ~/.bashrc
   source ~/.bashrc
   ```

### 4. Install Ruby
1. Install Ruby using Mise:
   ```sh
   mise use --global ruby@3
   ```
2. Verify the installation:
   ```sh
   ruby --version
   ```

### 5. Install Rails
1. Install Rails using the following command:
   ```sh
   gem install rails
   ```
2. Verify the installation:
   ```sh
   rails --version
   ```

### 6. Set Up Git
1. Install Git if it's not already installed:
   ```sh
   sudo apt install git
   ```
2. Configure Git with your username and email:
   ```sh
   git config --global user.name "YOUR NAME"
   git config --global user.email "YOUR@EMAIL.com"
   ```

### 7. Create a New Rails Project
1. Create a new Rails project:
   ```sh
   rails new myrailsapp
   cd myrailsapp
   ```

### 8. Run the Rails Server
1. Start the Rails server:
   ```sh
   rails server
   ```
2. Open your web browser and go to `http://localhost:3000` to see the Rails welcome page.

## Conclusion
Congratulations! You have successfully installed Ruby on Rails on your Ubuntu system. You can now start building and running Rails applications.

### Additional Resources
- [Ruby on Rails Guides](https://guides.rubyonrails.org/install_ruby_on_rails.html)
- [GoRails Setup Guide](https://gorails.com/setup/ubuntu/20.04)
