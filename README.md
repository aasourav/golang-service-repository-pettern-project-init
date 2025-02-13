# Go Application Boilerplate Setup

This repository provides a shell script to generate a standard boilerplate structure for building scalable Go applications. The generated structure is modular, maintainable, and ready for expansion as your project grows.

## Directory Structure

The script will create the following directory structure:
```bash
myapp/
├── cmd/
│ └── go-myapp-apis/
│ └── main.go
├── docs/
│ ├── docs.go
│ ├── swagger.json
│ └── swagger.yaml
├── go.mod
├── go.sum
├── internal/
│ └── config/
│ └── config.go
└── pkg/
├── handlers/
│ ├── app_authentication.go
│ ├── main_handler.go
│ ├── register_handler.go
│ ├── store_app_handler.go
│ ├── swagger.go
│ └── user_handler.go
├── interfaces/
│ ├── app_authentication_interface.go
│ └── register_interface.go
├── models/
│ ├── app_authentication_models.go
│ ├── register_models.go
├── repository/
│ ├── app_authentication_repository.go
│ ├── register_repository.go
│ ├── repository.go
│ ├── store_app_repository.go
├── routes/
│ └── user-routes.go
├── services/
│ ├── app_authentication_service.go
│ ├── register_service.go
│ ├── store_app_service.go
└── utils/
├── db.go
├── errors.go
├── helpers.go
├── social_login.go
└── token_utils.go
setup_project.sh
```

## Prerequisites

- **Bash**: Ensure you have a bash-compatible shell installed. This script is designed to run on Unix-like systems (Linux, macOS). 
- **Go**: Ensure you have Go installed on your machine.

## Installation

1. Clone the repository to your local machine:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
   
2. Make the setup_project.sh script executable:
   ```bash 
   chmod +x setup_project.sh
   ```
   
## Usage
1. Run the setup_project.sh script to generate the project structure:
```bash
./setup_project.sh
```
2. After running the script, you will find a new directory named myapp containing the predefined project structure.

## Customization
Feel free to modify the script or the generated files to better suit your project's specific requirements. The script is a starting point, and you can adapt it as your project grows.

## Contributing
If you find any issues with the script or have suggestions for improvement, feel free to open an issue or submit a pull request.



## Explanation :

# Project Structure

## 1. `cmd/` (Entry Point)
- The `main.go` file inside `cmd/go-myapp-apis/` is the **entry point** of your application.
- This is where you initialize the application by:
  - Loading configurations (`internal/config`).
  - Connecting to databases (`utils/db.go`).
  - Registering routes (`routes/`).
  - Starting the HTTP server (Gin Gonic or any framework you're using).

## 2. `internal/config/` (Configuration Management)
- Contains `config.go`, which loads environment variables, config files, and other app configurations.

## 3. `pkg/handlers/` (HTTP Handlers)
- Handles HTTP requests and responses.
- Uses services (`services/`) to process business logic.
- Example: `register_handler.go` handles user registration requests.

## 4. `pkg/interfaces/` (Interfaces for Dependency Injection)
- Defines contracts/interfaces that repositories and services must implement.
- Helps in unit testing and flexibility.

## 5. `pkg/models/` (Data Models)
- Defines the structures/models representing data (MongoDB, SQL tables, or any data format).
- Example: `register_models.go` might define `User` struct.

## 6. `pkg/repository/` (Data Access Layer - DAL)
- Responsible for interacting with the database.
- Implements CRUD operations.
- Example: `register_repository.go` contains functions like `CreateUser`, `GetUserByEmail`.

## 7. `pkg/services/` (Business Logic Layer)
- Implements core business logic.
- Uses repositories (`pkg/repository/`) to fetch/store data.
- Example: `register_service.go` contains `RegisterUser` function, which validates and processes the request before calling `register_repository.CreateUser`.

## 8. `pkg/routes/` (Routing Layer)
- Defines API routes and maps them to handlers.
- Example: `user-routes.go` registers user-related endpoints.

## 9. `pkg/utils/` (Utility Functions)
- Contains helper functions for common tasks like:
  - **Database connection** (`db.go`)
  - **Error handling** (`errors.go`)
  - **JWT token generation** (`token_utils.go`)
  - **Social login helpers** (`social_login.go`)

## How to Use This Structure in Your New Project?
1. **Define your models first** in `pkg/models/`
2. **Implement repository methods** in `pkg/repository/`
3. **Write business logic** in `pkg/services/`
4. **Create handlers** in `pkg/handlers/` to expose APIs
5. **Define routes** in `pkg/routes/`
6. **Write utility functions** in `pkg/utils/` for reusable logic


