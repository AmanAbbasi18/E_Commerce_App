# E-Commerce API

A RESTful API for managing e-commerce products and categories, built using Spring Boot, Spring Data JPA, and MySQL.

## Tech Stack

- **Language:** Java 17
- **Framework:** Spring Boot 3.3.4
- **Web:** Spring Web (REST APIs)
- **ORM:** Spring Data JPA, Hibernate
- **Database:** MySQL
- **Validation:** Jakarta Bean Validation
- **Build Tool:** Maven
- **Utilities:** Lombok

## Prerequisites

Make sure you have the following installed:

- Java 17 or later
- MySQL Server
- Maven (optional if using the included Maven Wrapper)

## Getting Started

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
cd E-Commerce-API
```

### 2. Create the MySQL Database

Start your MySQL server and execute the following SQL statement:

```sql
CREATE DATABASE ecommerce;
```

### 3. Configure Database Credentials

The application uses environment variables for database configuration. By default, it connects to a local MySQL instance.

| Environment Variable | Default Value | Description |
|---|---|---|
| `DB_HOST` | `localhost` | MySQL server hostname |
| `DB_PORT` | `3306` | MySQL server port |
| `DB_NAME` | `ecommerce` | Database name |
| `DB_USERNAME` | `root` | MySQL username |
| `DB_PASSWORD` | `root` | MySQL password |
| `SERVER_PORT` | `8080` | Application server port |

**Important:** Update `DB_USERNAME` and `DB_PASSWORD` to match your MySQL credentials. The default values are examples and must match your local setup.

You can configure these variables in your IDE's run configuration or your operating system's environment variables.

### 4. Run the Application

Using the Maven Wrapper on Windows:

```bash
mvnw.cmd spring-boot:run
```

On Linux or macOS:

```bash
./mvnw spring-boot:run
```

Alternatively, if Maven is installed:

```bash
mvn spring-boot:run
```

The application will start at:

`http://localhost:8080`

Hibernate automatically creates or updates database tables on startup using the configured `spring.jpa.hibernate.ddl-auto=update` setting.

## API Documentation

Base URL: `http://localhost:8080`

### Categories API

Base path: `/api/categories`

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/categories` | Retrieve all categories |
| GET | `/api/categories/{id}` | Retrieve a category by ID |
| POST | `/api/categories` | Create a category |
| PUT | `/api/categories/{id}` | Update a category |
| DELETE | `/api/categories/{id}` | Delete a category |

#### Example Request — Create a Category

```json
{
  "name": "Electronics",
  "description": "Phones, laptops and accessories"
}
```

### Products API

Base path: `/api/products`

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/products` | Retrieve products with pagination |
| GET | `/api/products/{id}` | Retrieve a product by ID |
| POST | `/api/products` | Create a product |
| PUT | `/api/products/{id}` | Update a product |
| DELETE | `/api/products/{id}` | Delete a product |

The product listing endpoint supports the following query parameters:

- `categoryId` — Filter products by category.
- `name` — Filter products by name.
- `page` — Specify the page number.
- `size` — Specify the number of products per page.
- `sort` — Specify sorting criteria.

#### Example Request — Create a Product

```json
{
  "name": "Wireless Mouse",
  "description": "2.4GHz wireless mouse",
  "price": 19.99,
  "stockQuantity": 100,
  "sku": "WM-1001",
  "categoryId": 1
}
```

## Error Handling

The API returns structured JSON responses for errors.

Example:

```json
{
  "timestamp": "2026-09-25T12:00:00",
  "status": 404,
  "error": "Not Found",
  "message": "Product not found with id: 42",
  "path": "/api/products/42"
}
```

## Database Configuration

The application connects to MySQL using the MySQL Connector/J JDBC driver and Spring Data JPA.

Database connection settings can be customized through environment variables without modifying the application code.

**Note:** The `update` schema strategy is intended for development. For production deployments, consider using a database migration tool such as Flyway or Liquibase.

## License

Add your chosen license information here if the project is distributed under an open-source license.
