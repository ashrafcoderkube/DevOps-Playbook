# Ruby on Rails Installation Guide for macOS

## Prerequisites
- macOS 10.13 or higher
- An active internet connection

## Step-by-Step Installation

### 1. Install Homebrew (Package Manager)
1. Open the Terminal application. You can find it in `Applications` > `Utilities` > `Terminal`.
2. Install Homebrew by running the following command:
   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

### 2. Install Ruby using Homebrew
1. Install Ruby using Homebrew by running the following command:
   ```sh
   brew install ruby
   ```
2. Verify the installation:
   ```sh
   ruby --version
   ```

### 3. Configure RubyGems
1. Add the following line to your shell configuration file (e.g., `.zshrc` or `.bash_profile`):
   ```sh
   export PATH="/usr/local/opt/ruby/bin:$PATH"
   ```
2. Source the configuration file to apply the changes:
   ```sh
   source ~/.zshrc
   ```
   or
   ```sh
   source ~/.bash_profile
   ```

### 4. Install Rails
1. Install Rails using the following command:
   ```sh
   gem install rails
   ```
2. Verify the installation:
   ```sh
   rails --version
   ```

### 5. Set Up Git
1. Install Git if it's not already installed:
   ```sh
   brew install git
   ```
2. Configure Git with your username and email:
   ```sh
   git config --global user.name "YOUR NAME"
   git config --global user.email "YOUR@EMAIL.com"
   ```

### 6. Create a New Rails Project
1. Create a new Rails project:
   ```sh
   rails new myrailsapp
   cd myrailsapp
   ```

### 7. Run the Rails Server
1. Start the Rails server:
   ```sh
   rails server
   ```
2. Open your web browser and go to `http://localhost:3000` to see the Rails welcome page.

## Conclusion
Congratulations! You have successfully installed Ruby on Rails on your macOS system. You can now start building and running Rails applications.

### Additional Resources
- [Ruby on Rails Guides](https://guides.rubyonrails.org/install_ruby_on_rails.html)
- [GoRails Setup Guide](https://gorails.com/setup/osx/10.15-catalina)
