Here’s a complete `README.md` for your **Product API** project:

---

# **Product API**

This is a RESTful API for managing products, built with **Gin** and **GORM**. It provides endpoints to create, retrieve, update, and delete product information, with SQLite as the database.

---

## **Features**
- **Add a Product**: Add new products to the database.
- **Retrieve Products**: Fetch all or individual product details.
- **Update a Product**: Modify product information.
- **Delete a Product**: Remove a product from the database.

---

## **Technologies Used**
- **Go**: Programming language.
- **Gin**: Web framework for building RESTful APIs.
- **GORM**: ORM library for database interactions.
- **SQLite**: Lightweight database for data storage.

---

## **Project Structure**
```
product_api/
├── main.go            # Main application file
├── go.mod             # Go module file
├── go.sum             # Dependencies file
└── products.db        # SQLite database file (auto-created)
```

---

## **Endpoints**

### **Base URL**
```
http://localhost:8080
```

---

### **1. Get All Products**
- **URL**: `/products`
- **Method**: `GET`
- **Description**: Retrieve a list of all products.
- **Response Example**:
  ```json
  [
    {
      "id": 1,
      "name": "Sample Product",
      "price": 100.0,
      "stock": 20
    },
    {
      "id": 2,
      "name": "Another Product",
      "price": 50.0,
      "stock": 10
    }
  ]
  ```

---

### **2. Get Product by ID**
- **URL**: `/products/{id}`
- **Method**: `GET`
- **Description**: Fetch a specific product by its ID.
- **Response Example**:
  ```json
  {
    "id": 1,
    "name": "Sample Product",
    "price": 100.0,
    "stock": 20
  }
  ```

If the product doesn’t exist:
```json
{
  "error": "Product not found"
}
```

---

### **3. Add a Product**
- **URL**: `/products`
- **Method**: `POST`
- **Description**: Add a new product to the database.
- **Request Body Example**:
  ```json
  {
    "name": "New Product",
    "price": 150.0,
    "stock": 30
  }
  ```
- **Response Example**:
  ```json
  {
    "id": 3,
    "name": "New Product",
    "price": 150.0,
    "stock": 30
  }
  ```

---

### **4. Update a Product**
- **URL**: `/products/{id}`
- **Method**: `PUT`
- **Description**: Update an existing product's details.
- **Request Body Example**:
  ```json
  {
    "name": "Updated Product",
    "price": 120.0,
    "stock": 15
  }
  ```
- **Response Example**:
  ```json
  {
    "id": 1,
    "name": "Updated Product",
    "price": 120.0,
    "stock": 15
  }
  ```

---

### **5. Delete a Product**
- **URL**: `/products/{id}`
- **Method**: `DELETE`
- **Description**: Delete a product by its ID.
- **Response Example**:
  ```json
  {
    "message": "Product deleted"
  }
  ```

---

## **Setup Instructions**

### **1. Prerequisites**
- Install **Go**: [Download and install Go](https://go.dev/dl/).

### **2. Clone the Repository**
```bash
git clone https://github.com/your-username/product_api.git
cd product_api
```

### **3. Install Dependencies**
```bash
go mod tidy
```

### **4. Run the Server**
```bash
go run main.go
```

The server will start on `http://localhost:8080`.

---

## **Testing the API**

### **Using cURL**
- **Add a Product**:
  ```bash
  curl -X POST -H "Content-Type: application/json" -d '{"name":"Sample Product","price":100.0,"stock":20}' http://localhost:8080/products
  ```

- **Get All Products**:
  ```bash
  curl http://localhost:8080/products
  ```

- **Get a Product by ID**:
  ```bash
  curl http://localhost:8080/products/1
  ```

- **Update a Product**:
  ```bash
  curl -X PUT -H "Content-Type: application/json" -d '{"name":"Updated Product","price":120.0,"stock":15}' http://localhost:8080/products/1
  ```

- **Delete a Product**:
  ```bash
  curl -X DELETE http://localhost:8080/products/1
  ```

---

### **Using Postman**
1. Open Postman and create a new request.
2. Select the appropriate HTTP method (`GET`, `POST`, `PUT`, or `DELETE`).
3. Set the request URL to `http://localhost:8080/products` or `/products/{id}`.
4. Add a JSON body for `POST` and `PUT` requests.

---

## **Database Information**
- **Database**: SQLite
- **File**: `products.db`
- Automatically created when the server runs for the first time.
- To view or query the database, use the SQLite CLI:
  ```bash
  sqlite3 products.db
  ```

---

## **Future Enhancements**
- Add **input validation** to ensure data integrity.
- Implement **pagination** for the `/products` endpoint.
- Add **authentication** and **authorization** (e.g., using JWT).
- Integrate with a more scalable database (e.g., PostgreSQL).

---

## **License**
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
