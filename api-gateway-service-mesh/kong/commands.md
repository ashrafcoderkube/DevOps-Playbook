
<img src="assets/image.png" alt="kong" width="250" >

## **Kong API Gateway Commands (Quick Reference)**  

## **1. Starting, Stopping, and Managing Kong**  

### **Start Kong**  
```bash
kong start
```

### **Restart Kong**  
```bash
kong restart
```

### **Stop Kong**  
```bash
kong stop
```

### **Check Kong Status**  
```bash
kong health
```

### **Check Kong Version**  
```bash
kong version
```

### **Validate Kong Configuration**  
```bash
kong check
```

### **Reload Kong Configuration (without downtime)**  
```bash
kong reload
```

---

## **2. Service and Route Management**  

### **Create a Service**  
```bash
curl -i -X POST http://localhost:8001/services \
  --data name=myservice \
  --data url=http://example.com
```

### **List Services**  
```bash
curl -i -X GET http://localhost:8001/services
```

### **Delete a Service**  
```bash
curl -i -X DELETE http://localhost:8001/services/myservice
```

### **Create a Route for a Service**  
```bash
curl -i -X POST http://localhost:8001/services/myservice/routes \
  --data paths[]=/myapi
```

### **List Routes**  
```bash
curl -i -X GET http://localhost:8001/routes
```

### **Delete a Route**  
```bash
curl -i -X DELETE http://localhost:8001/routes/<route_id>
```

---

## **3. Plugin Management**  

### **Enable Rate Limiting Plugin**  
```bash
curl -X POST http://localhost:8001/services/myservice/plugins \
  --data "name=rate-limiting" \
  --data "config.second=5"
```

### **Enable JWT Authentication Plugin**  
```bash
curl -X POST http://localhost:8001/services/myservice/plugins \
  --data "name=jwt"
```

### **Enable Key Authentication Plugin**  
```bash
curl -X POST http://localhost:8001/services/myservice/plugins \
  --data "name=key-auth"
```

### **List Enabled Plugins**  
```bash
curl -X GET http://localhost:8001/plugins
```

### **Delete a Plugin**  
```bash
curl -X DELETE http://localhost:8001/plugins/<plugin_id>
```

---

## **4. Consumer Management**  

### **Create a Consumer**  
```bash
curl -i -X POST http://localhost:8001/consumers \
  --data "username=user1"
```

### **List Consumers**  
```bash
curl -i -X GET http://localhost:8001/consumers
```

### **Generate API Key for a Consumer**  
```bash
curl -i -X POST http://localhost:8001/consumers/user1/key-auth
```

### **List API Keys for a Consumer**  
```bash
curl -i -X GET http://localhost:8001/consumers/user1/key-auth
```

### **Delete a Consumer**  
```bash
curl -i -X DELETE http://localhost:8001/consumers/user1
```

---

## **5. Admin API Commands**  

### **List All Services**  
```bash
curl -X GET http://localhost:8001/services
```

### **Check Kong Gateway Health**  
```bash
curl -X GET http://localhost:8001/status
```

### **List All Plugins Installed**  
```bash
curl -X GET http://localhost:8001/plugins
```

### **Check Node Status**  
```bash
curl -X GET http://localhost:8001/status
```

---

## **6. Logging & Debugging**  

### **View Kong Logs (Docker)**  
```bash
docker logs -f kong
```

### **Check Kong Configuration Issues**  
```bash
kong check
```

---

## **7. Database Management**  

### **Run Kong Migrations (PostgreSQL mode)**  
```bash
kong migrations bootstrap
```

### **Reset Kong Database (Destructive)**  
```bash
kong migrations reset
```

### **Apply Database Migrations**  
```bash
kong migrations up
```

---

## **8. Docker Commands for Kong**  

### **Pull Kong Docker Image**  
```bash
docker pull kong
```

### **Run Kong with Database (PostgreSQL)**  
```bash
docker run -d --name kong \
  --link kong-database:kong-database \
  -e KONG_DATABASE=postgres \
  -e KONG_PG_HOST=kong-database \
  -p 8000:8000 \
  -p 8001:8001 \
  kong
```

### **Run Kong in DB-less Mode**  
```bash
docker run -d --name kong \
  -e KONG_DATABASE=off \
  -e KONG_DECLARATIVE_CONFIG=/path/to/kong.yml \
  -p 8000:8000 \
  -p 8001:8001 \
  kong
```

---

## **9. Kubernetes Commands (if using Kong Ingress Controller)**  

### **Install Kong Ingress via Helm**  
```bash
helm install kong kong/kong --set ingressController.installCRDs=false
```

### **Check Kong Ingress Status**  
```bash
kubectl get pods -n kong
```

### **Delete Kong Ingress**  
```bash
helm delete kong
```

---

## **Documentation Links**  

- **Kong Admin API Reference** → [https://docs.konghq.com/gateway/latest/admin-api/](https://docs.konghq.com/gateway/latest/admin-api/)  
- **Kong Plugin Hub** → [https://docs.konghq.com/hub/](https://docs.konghq.com/hub/)  
- **Kong Configuration Reference** → [https://docs.konghq.com/gateway/latest/configuration/](https://docs.konghq.com/gateway/latest/configuration/)  

---
