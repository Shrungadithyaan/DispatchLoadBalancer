# Dispatch Load Balancer - Spring Boot Application



This project is a **Spring Boot application** designed to optimize the allocation of delivery orders to a fleet of vehicles based on their locations. The goal is to minimize the total travel distance while considering vehicle capacities and order priorities. The application utilizes the **Haversine formula** to calculate distances between geographic coordinates.

---

## **Technologies Used**
- **Java** 17
- **Spring Boot** 3.1.0
- **H2 Database** 2.1.2 (in-memory database for local development and testing)
- **Maven** 3.x (for dependency management)
- **Mockito** 5.x (for unit testing)
- **Swagger** (for API documentation)
- **Postman** (for API testing)

---

## **Features**
1. **Order Management**
   - Accepts delivery orders with details like `orderId`, `latitude`, `longitude`, `address`, `packageWeight`, and `priority`.
2. **Vehicle Management**
   - Accepts vehicle details with `vehicleId`, `capacity`, `currentLatitude`, `currentLongitude`, and `currentAddress`.
3. **Dispatch Optimization**
   - Assigns orders to vehicles based on **priority** and **capacity**.
   - Minimizes total travel distance using the **Haversine formula**.
4. **Error Handling**
   - Handles invalid input, overcapacity scenarios, and unassignable orders gracefully.

---

## **Implementation Details**

The application calculates distances using the **Haversine formula** and follows an order allocation strategy based on:
- **Priority**: High-priority orders are assigned first.
- **Capacity**: Orders are assigned to vehicles without exceeding their capacity.
- **Distance**: Orders are assigned to the closest available vehicle.

---

## **How to Run the Project**

### **Prerequisites**
- **Java 17** installed
- **Maven** installed

### **Steps to Run**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Shrungadithyaan/DispatchLoadBalancer.git
   cd DispatchLoadBalancer
   ```

2. **Build the Project**:
   ```bash
   mvn clean install
   ```

3. **Run the Application**:
   ```bash
   mvn spring-boot:run
   ```

4. **Access the Application**:
   - Application runs at: `http://localhost:8080`
   - Swagger UI: `http://localhost:8080/swagger-ui.html`

5. **Run Tests**:
   To execute unit tests, run the following command:
   
   ```bash
   mvn test
   ```
---

## **API Endpoints**

### **1. Input Delivery Orders**
- **Endpoint**: `POST /api/dispatch/orders`
- **Request Body**:
  ```json
  {
    "orders": [
      {
        "orderId": "ORD001",
        "latitude": 12.2958,
        "longitude": 76.6394,
        "address": "MG Road, Mysore",
        "packageWeight": 10,
        "priority": "HIGH"
      }
    ]
  }
  ```
- **Response**:
  ```json
  {
    "message": "Delivery orders accepted.",
    "status": "success"
  }
  ```

### **2. Input Fleet Details**
- **Endpoint**: `POST /api/dispatch/vehicles`
- **Request Body**:
  ```json
  {
    "vehicles": [
      {
        "vehicleId": "VEH001",
        "capacity": 100,
        "currentLatitude": 12.3180,
        "currentLongitude": 76.6548,
        "currentAddress": "Vijayanagar, Mysore"
      }
    ]
  }
  ```
- **Response**:
  ```json
  {
    "message": "Vehicle details accepted.",
    "status": "success"
  }
  ```

### **3. Retrieve Dispatch Plan**
- **Endpoint**: `GET /api/dispatch/plan`
- **Response**:
  ```json
  {
    "status": "success",
    "message": "All orders assigned successfully",
    "dispatchPlan": [
      {
        "vehicleId": "VEH001",
        "totalLoad": 10,
        "totalDistance": "5.25 km",
        "assignedOrders": [
          {
            "orderId": "ORD001",
            "latitude": 12.2958,
            "longitude": 76.6394,
            "address": "MG Road, Mysore",
            "packageWeight": 10,
            "priority": "HIGH"
          }
        ]
      }
    ],
    "unassignedOrders": []
  }
  ```

---

## **File Structure**
```
dispatch-load-balancer/
├── src/
│   ├── main/
│   │   ├── java/com/dispatch/dispatchloadbalancer/
│   │   │   ├── config/
│   │   │   ├── controller/
│   │   │   ├── dto/
│   │   │   ├── exception/
│   │   │   ├── service/
│   │   │   ├── repository/
│   │   │   ├── model/
│   │   │   ├── util/
│   │   │   └── DispatchLoadBalancerApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── data.sql
│   └── test/java/com/dispatch/dispatchloadbalancer/
│       ├── controller/
│       ├── service/
│       └── DispatchLoadBalancerApplicationTests.java
├── pom.xml
└── README.md
```



---

## **Output**


[![Image 1](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/1c.png?raw=true)](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/1c.png?raw=true)

[![Image 2](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/2c.png?raw=true)](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/2c.png?raw=true)

[![Image 3](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/3c.png?raw=true)](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/3c.png?raw=true)

[![Image 4](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/5c.png?raw=true)](https://github.com/Shrungadithyaan/DispatchLoadBalancer/blob/main/output_IMG/5c.png?raw=true)

---

## **Reference Links**
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/index.html)
- [Java Enum Reference](https://www.w3schools.com/java/ref_keyword_enum.asp)
- [Java Documentation](https://www.tutorialspoint.com/java/java_documentation.htm)
- [Maven POM Guide](https://maven.apache.org/pom.html)

---

## **Contact**
For any questions or issues, please contact:

- **Name**: Shrungadithya A N
- **Email**: shrungadithyaan@gmail.com
- **GitHub**: [Shrungadithyaan](https://github.com/Shrungadithyaan)
- **Portfolio**: [shrungadithya.netlify.app](https://shrungadithya.netlify.app/)
