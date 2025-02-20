## Ruby on Rails Commands (macOS)

### Project Commands
- **Create a new Rails project:**
  ```sh
  rails new projectname
  ```
  Replace `projectname` with your desired project name.

- **Generate scaffolding for a resource:**
  ```sh
  rails generate scaffold ResourceName attribute:type
  ```

- **Generate a controller:**
  ```sh
  rails generate controller ControllerName actions
  ```

- **Generate a model:**
  ```sh
  rails generate model ModelName attribute:type
  ```

### Database Commands
- **Create and set up the database:**
  ```sh
  rails db:create
  rails db:migrate
  ```

- **Migrate the database:**
  ```sh
  rails db:migrate
  ```

- **Rollback the last migration:**
  ```sh
  rails db:rollback
  ```

### Server Commands
- **Start the Rails server:**
  ```sh
  rails server
  ```

- **Run the Rails console:**
  ```sh
  rails console
  ```

- **Open the Rails database console:**
  ```sh
  rails dbconsole
  ```

### Testing Commands
- **Run tests:**
  ```sh
  rails test
  ```

- **Generate test scaffolding:**
  ```sh
  rails generate test_unit:scaffold ModelName
  ```

### Asset Commands
- **Precompile assets:**
  ```sh
  rails assets:precompile
  ```

- **Clean compiled assets:**
  ```sh
  rails assets:clean
  ```

### Environment Variables
- **Set the Rails environment:**
  ```sh
  export RAILS_ENV=production
  ```

These commands will help you manage your Ruby on Rails projects on macOS. 