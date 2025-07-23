# Employee Management System (Spring Boot + React)

## Project Overview

This repository contains a full-stack **Employee Management System** web application. It consists of a Spring Boot backend (Java) that exposes RESTful APIs with Spring Data JPA and MySQL for data persistence, and a React frontend (JavaScript) built with Vite and styled using Bootstrap. The core purpose of the project is to allow users to manage employee records – providing functionality to create, read, update, and delete employee information via a user-friendly web interface.

## Features

- **Employee CRUD Operations:** Users can list all employees, add new employee records, update existing employee details, and delete employees. Each employee has a first name, last name, and email address.
- **RESTful API:** The backend provides a REST API for all employee operations (GET, POST, PUT, DELETE), allowing integration or testing with tools like Postman.
- **Responsive Frontend:** The frontend is a single-page application built with React. It uses React Router for navigation (list view, add/edit form) and Bootstrap for a responsive layout and styling.
- **Error Handling & Notifications:** The application uses Axios for HTTP requests and basic error handling in the frontend (e.g., logging errors to console). It also incorporates user feedback via forms and may use libraries like React Toastify for notifications (installed in dependencies).
- **Persistent Storage:** Employee data is stored in a MySQL database on the backend, so all changes (adds/edits/deletes) persist across server restarts. The Spring JPA layer auto-creates the `employees` table and manages records.

## Technology Stack

- **Backend:** Spring Boot 3.x, Spring Data JPA, MySQL, Lombok, Maven, Java 17
- **Frontend:** React 18, React Router, Vite, Axios, Bootstrap 5, JavaScript (ES6+)

## Project Structure

```plaintext
- ems-backend/        # Spring Boot backend (Java, Maven project)
- ems-frontend/       # React frontend (JavaScript, Vite project)
```

## Installation

### Backend Setup (Spring Boot API)

#### Prerequisites:
- Java 17+
- Maven
- MySQL

#### Steps:
1. **Create MySQL Database**
   ```sql
   CREATE DATABASE ems;
   ```

2. **Configure Database**
   Edit `ems-backend/src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/ems
   spring.datasource.username=root
   spring.datasource.password=your_password
   spring.jpa.hibernate.ddl-auto=update
   ```

3. **Run Backend**
   ```bash
   cd ems-backend
   ./mvnw spring-boot:run
   ```

### Frontend Setup (React App)

#### Prerequisites:
- Node.js v14+
- npm

#### Steps:
1. **Install Dependencies**
   ```bash
   cd ems-frontend
   npm install
   ```

2. **Run Frontend**
   ```bash
   npm run dev
   ```

3. **Visit**
   Open browser at [http://localhost:3000](http://localhost:3000)

## Configuration

### Backend
- `server.port=8080` (default)
- MySQL credentials in `application.properties`
- `spring.jpa.hibernate.ddl-auto=update`

### Frontend
Update `REST_API_BASE_URL` in `src/services/EmployeeService.js` if backend URL changes.

## Usage

- Visit [http://localhost:3000](http://localhost:3000)
- Use "Add Employee" to create records
- Use "Update" and "Delete" for existing records
- Data persists via MySQL backend

## API Documentation

| Method | Endpoint                 | Description                   |
|--------|--------------------------|-------------------------------|
| GET    | `/api/employees`         | Fetch all employees           |
| POST   | `/api/employees`         | Add a new employee            |
| GET    | `/api/employees/{id}`    | Get employee by ID            |
| PUT    | `/api/employees/{id}`    | Update employee by ID         |
| DELETE | `/api/employees/{id}`    | Delete employee by ID         |

## Testing

### Backend
Run:
```bash
cd ems-backend
mvn test
```

Includes basic Spring Boot JUnit tests. Extend as needed for services/controllers.

### Frontend
No test suite configured by default. Manual testing recommended.

## Deployment

### Backend
1. Build JAR:
   ```bash
   mvn package
   ```
2. Run:
   ```bash
   java -jar target/ems-backend-0.0.1-SNAPSHOT.jar
   ```

3. Deploy to: Heroku, AWS, Azure, or Docker.

### Frontend
1. Build:
   ```bash
   npm run build
   ```

2. Serve `dist/` via:
   - Static hosting: Netlify, Vercel, GitHub Pages
   - Spring Boot: Copy `dist/` to `ems-backend/src/main/resources/static`
   - Docker + Nginx

### Database
Set up MySQL on production server. Ensure secure credential management.

## Contributing

1. Fork repo and create feature branch.
2. Submit a pull request with a clear description.
3. Follow coding conventions and add tests where appropriate.
4. For large changes, open an issue for discussion first.

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
