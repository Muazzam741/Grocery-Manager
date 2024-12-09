
# **Grocery Management Web Application**

A lightweight web application for managing grocery store inventory, tracking orders, and performing CRUD operations. Built using Flask for the backend, MySQL for the database, and supporting APIs for integration.

---

## **Features**
- **Manage Products**: Add, view, and delete grocery items.
- **Orders Management**: Create and view customer orders.
- **Units of Measure (UOM)**: Retrieve and manage units of measure.
- **RESTful APIs**: Provides APIs for integration with frontend or other systems.
- **CORS Enabled**: Allows cross-origin requests for flexibility in integration.

---

## **Tech Stack**
### Backend:
- **Flask**: For routing and REST API handling.
- **MySQL**: For database management.

### Tools:
- **MySQL Connector**: For connecting Flask with MySQL.
- **Postman**: For testing APIs (optional).

---

## **Installation**

### **1. Clone the Repository**
```bash
git clone https://github.com/Muazzam741/Grocery-Manager.git
```

### **2. Set Up Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### **3. Install Dependencies**
```bash
pip install -r requirements.txt
```

### **4. Set Up the Database**
1. Create a MySQL database:
   ```sql
   CREATE DATABASE grocery_store;
   ```
2. Import the schema:
   ```bash
   mysql -u your_username -p grocery_store < schema.sql
   ```

### **5. Configure Database Connection**
Update the `sql_connection.py` file to include your MySQL credentials:
```python
def get_sql_connection():
    return mysql.connector.connect(
        host='localhost',
        user='your_username',
        password='your_password',
        database='grocery_store'
    )
```

### **6. Run the Application**
```bash
python app.py
```
Access the app at `http://127.0.0.1:5000`.

---

## **API Endpoints**
| **Endpoint**          | **Method** | **Description**                     | **Request Data**        |
|------------------------|------------|-------------------------------------|-------------------------|
| `/getUOM`             | GET        | Retrieve all units of measure       | -                       |
| `/getProducts`        | GET        | Retrieve all products               | -                       |
| `/insertProduct`      | POST       | Add a new product                   | `data: JSON`            |
| `/getAllOrders`       | GET        | Retrieve all orders                 | -                       |
| `/insertOrder`        | POST       | Insert a new order                  | `data: JSON`            |
| `/deleteProduct`      | POST       | Delete a product by ID              | `product_id: string`    |

---

## **Example API Usage**

### **1. Add a Product**
- **Endpoint**: `/insertProduct`  
- **Method**: POST  
- **Request Data**:
  ```json
  {
      "name": "Apple",
      "price_per_unit": 50,
      "uom_id": 1
  }
  ```
- **Response**:
  ```json
  {
      "product_id": 101
  }
  ```

### **2. Get All Products**
- **Endpoint**: `/getProducts`  
- **Method**: GET  
- **Response**:
  ```json
  [
      {
          "id": 1,
          "name": "Apple",
          "price_per_unit": 50,
          "uom_id": 1
      },
      ...
  ]
  ```

### **3. Delete a Product**
- **Endpoint**: `/deleteProduct`  
- **Method**: POST  
- **Request Data**:
  ```json
  {
      "product_id": 101
  }
  ```
- **Response**:
  ```json
  {
      "product_id": 101
  }
  ```

---

## **Folder Structure**
```
grocery-management/
├── static/             # CSS, JavaScript, and images
├── templates/          # HTML files
├── app.py              # Main Flask application
├── sql_connection.py   # MySQL connection setup
├── products_dao.py     # Product data access object
├── orders_dao.py       # Order data access object
├── uom_dao.py          # Unit of measure data access object
├── schema.sql          # SQL schema for database
├── requirements.txt    # Python dependencies
├── README.md           # Project documentation
```

---

## **Future Enhancements**
- Integrate a user interface for easy interaction with APIs.
- Implement role-based user authentication.
- Add reporting and analytics dashboards.
- Include error handling for robust API interactions.

---

## **License**
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## **Contact**
For questions or support, please contact [muazzamali741@gmail.com](muazzamali741@gmail.com).
