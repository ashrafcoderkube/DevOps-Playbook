<img src="image.png" alt="kong" width="120" height="120">

## **Kong API Gateway**  

### **Overview**  
Kong is a high-performance, scalable, and open-source API Gateway and Microservices Management Layer. It provides security, authentication, rate limiting, logging, and other essential API management features.  

### **Key Features**  

- **Lightweight & Fast:** Built on Nginx and OpenResty for high performance.  
- **Scalable:** Can be deployed in distributed environments, including Kubernetes.  
- **Security:** Supports authentication, OAuth2, JWT, and ACLs.  
- **Plugins:** Offers a wide range of plugins for logging, rate limiting, and monitoring.  
- **Service Mesh Support:** Can be integrated into a service mesh architecture.  

---

### **Use Cases**  

- **API Gateway:** Securely expose microservices with Kong’s API management features.  
- **Traffic Control:** Manage request routing, authentication, and rate limiting.  
- **Security & Compliance:** Enforce API security policies using plugins.  
- **Monitoring & Analytics:** Use logging and monitoring plugins for insights.  
- **Service Mesh Support:** Deploy as a service mesh for microservices communication.  

---

## **Setting Up Kong**  

### **1. Prerequisites**  

- **Docker installed** (if using Docker setup).  
- **PostgreSQL or Cassandra** (for database-backed mode).  
- **Kong Gateway package** (for manual installation).  

---

### **2. Installing Kong**  

#### **a) Using Docker (Recommended)**  

1. **Pull the Kong Docker image**  
   ```bash
   docker pull kong
   ```

2. **Start PostgreSQL for Kong (if using a database)**  
   ```bash
   docker run -d --name kong-database \
     -p 5432:5432 \
     -e POSTGRES_USER=kong \
     -e POSTGRES_DB=kong \
     postgres
   ```

3. **Run Kong Migrations**  
   ```bash
   docker run --rm \
     --link kong-database:kong-database \
     -e KONG_DATABASE=postgres \
     -e KONG_PG_HOST=kong-database \
     kong kong migrations bootstrap
   ```

4. **Start Kong Gateway**  
   ```bash
   docker run -d --name kong \
     --link kong-database:kong-database \
     -e KONG_DATABASE=postgres \
     -e KONG_PG_HOST=kong-database \
     -p 8000:8000 \
     -p 8001:8001 \
     kong
   ```

---

#### **b) Installing Kong on Linux (Debian/Ubuntu)**  

1. **Add the Kong repository**  
   ```bash
   echo "deb https://download.konghq.com/gateway-3.x-ubuntu-focal all main" | sudo tee /etc/apt/sources.list.d/kong.list
   ```

2. **Install Kong**  
   ```bash
   sudo apt update && sudo apt install -y kong
   ```

3. **Start Kong**  
   ```bash
   sudo kong start
   ```

---

## **Kong API Gateway Commands**  

### **1. Starting and Stopping Kong**  

- **Start Kong**  
  ```bash
  kong start
  ```

- **Restart Kong**  
  ```bash
  kong restart
  ```

- **Stop Kong**  
  ```bash
  kong stop
  ```

- **Check Kong status**  
  ```bash
  kong health
  ```

---

### **2. Configuring Services and Routes**  

- **Add a Service**  
  ```bash
  curl -i -X POST http://localhost:8001/services \
    --data name=myservice \
    --data url=http://example.com
  ```

- **List Services**  
  ```bash
  curl -i -X GET http://localhost:8001/services
  ```

- **Delete a Service**  
  ```bash
  curl -i -X DELETE http://localhost:8001/services/myservice
  ```

- **Add a Route**  
  ```bash
  curl -i -X POST http://localhost:8001/services/myservice/routes \
    --data paths[]=/myapi
  ```

- **List Routes**  
  ```bash
  curl -i -X GET http://localhost:8001/routes
  ```

---

### **3. Managing Plugins**  

- **Enable Rate Limiting Plugin**  
  ```bash
  curl -X POST http://localhost:8001/services/myservice/plugins \
    --data "name=rate-limiting" \
    --data "config.second=5"
  ```

- **Enable Key Authentication Plugin**  
  ```bash
  curl -X POST http://localhost:8001/services/myservice/plugins \
    --data "name=key-auth"
  ```

- **List Enabled Plugins**  
  ```bash
  curl -X GET http://localhost:8001/plugins
  ```

---

### **4. Managing Consumers**  

- **Create a Consumer**  
  ```bash
  curl -i -X POST http://localhost:8001/consumers \
    --data "username=user1"
  ```

- **List Consumers**  
  ```bash
  curl -i -X GET http://localhost:8001/consumers
  ```

- **Generate API Key for a Consumer**  
  ```bash
  curl -i -X POST http://localhost:8001/consumers/user1/key-auth
  ```

- **List API Keys for a Consumer**  
  ```bash
  curl -i -X GET http://localhost:8001/consumers/user1/key-auth
  ```

---

### **5. Logging and Debugging**  

- **View Kong Logs (Docker)**  
  ```bash
  docker logs -f kong
  ```

- **Check Kong Version**  
  ```bash
  kong version
  ```

- **Check Configuration Issues**  
  ```bash
  kong check
  ```

---

### **6. Kong Admin API Endpoints**  

- **List All Kong Services**  
  ```bash
  curl -X GET http://localhost:8001/services
  ```

- **Check Kong Gateway Health**  
  ```bash
  curl -X GET http://localhost:8001/status
  ```

- **List All Plugins Installed**  
  ```bash
  curl -X GET http://localhost:8001/plugins
  ```

---

## **Kong Documentation & Additional Resources**  

- **Official Kong Docs** → [https://docs.konghq.com/](https://docs.konghq.com/)  
- **Kong Admin API Reference** → [https://docs.konghq.com/gateway/latest/admin-api/](https://docs.konghq.com/gateway/latest/admin-api/)  
- **Kong Plugin Hub** → [https://docs.konghq.com/hub/](https://docs.konghq.com/hub/)  

---

### **Final Notes**  

- Kong is highly **configurable** and supports various **authentication mechanisms** (JWT, OAuth2, Basic Auth, API Keys, etc.).  
- It can be deployed **on-premise** or in **cloud-native environments** (Kubernetes, AWS, GCP, etc.).  
- Kong provides **enterprise versions** with additional features like **service mesh** and **analytics dashboards**.  

