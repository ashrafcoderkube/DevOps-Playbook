<img src="assets/image.png" alt="envoy" width="250" >


### **Envoy Proxy Theory**

Envoy is an open-source, high-performance proxy designed for modern cloud-native applications. It operates as a sidecar proxy within a microservices architecture and is often used alongside service meshes like Istio for advanced traffic management, observability, and security features.

#### **Key Features of Envoy:**

1. **L7 Proxying (Application Layer):** 
   Envoy is an advanced proxy that works at Layer 7 (the Application Layer) of the OSI model. It supports HTTP/1, HTTP/2, gRPC, and WebSockets, enabling sophisticated traffic management such as routing, load balancing, and service discovery.

2. **Load Balancing:**
   Envoy offers a wide range of load balancing algorithms (round-robin, least-connections, random, etc.) and advanced features like circuit breaking, retries, and fault injection to control the flow of traffic.

3. **Service Discovery and Routing:**
   Envoy can automatically discover services in a Kubernetes environment and route traffic based on service metadata. It also supports dynamic routing and versioned routing for managing deployments.

4. **Resiliency:**
   It provides advanced features such as circuit breaking, retries, timeouts, and rate-limiting to ensure that applications are resilient to failures and disruptions.

5. **Observability:**
   Envoy supports deep integration with observability tools like Prometheus, Grafana, and Jaeger for collecting metrics, logs, and traces. It helps monitor the health and performance of microservices.

6. **Security (mTLS):**
   Envoy can be configured with mutual TLS (mTLS) for service-to-service authentication and encryption, ensuring secure communication in a service mesh.

7. **Filters and Extensibility:**
   Envoy is highly extensible, with support for custom filters and plugins that can modify and manipulate traffic as it passes through the proxy. It allows for advanced customization of request/response processing.

8. **Istio Integration:**
   Envoy is commonly used as the data plane in Istio’s service mesh architecture. In this context, Envoy proxies sit alongside application containers and manage network traffic, enforce policies, and report telemetry data.

---

### **Envoy Proxy Commands**

Here are some common commands for managing and interacting with Envoy:

1. **Running Envoy as a Standalone Proxy:**

   To run Envoy with a configuration file (`envoy.yaml`), use the following command:
   ```bash
   envoy -c /path/to/envoy.yaml
   ```

2. **Run Envoy with Debug Logging:**

   To enable debug logging in Envoy:
   ```bash
   envoy -c /path/to/envoy.yaml --log-level debug
   ```

3. **Checking Envoy Version:**

   To check the current version of Envoy running:
   ```bash
   envoy --version
   ```

4. **Starting Envoy with a Specific Service Cluster Configuration:**

   Run Envoy to proxy requests for a specific service cluster defined in your configuration:
   ```bash
   envoy -c /path/to/service-cluster-config.yaml
   ```

5. **Viewing Envoy Stats:**

   Envoy exposes a `/stats` endpoint to collect internal metrics (via HTTP):
   ```bash
   curl http://localhost:8001/stats
   ```

6. **Viewing Envoy Configuration via Admin API:**

   You can view Envoy's current configuration using its Admin API:
   ```bash
   curl http://localhost:8001/config_dump
   ```

7. **Checking the Status of Envoy:**

   To check if Envoy is running, use the admin API or view the status:
   ```bash
   curl http://localhost:8001/server_info
   ```

8. **Reloading Envoy Configuration:**

   To apply changes to Envoy's configuration without restarting, send a SIGHUP signal:
   ```bash
   kill -SIGHUP <envoy_pid>
   ```

9. **Start Envoy with TLS Termination:**

   If you need to terminate TLS traffic and forward it to your backend services, you can configure Envoy like so:
   ```bash
   envoy -c /path/to/envoy-tls-config.yaml
   ```

10. **Running Envoy with XDS (Extensible Data Plane API):**

    Envoy can be integrated with a control plane using the XDS protocol. To start Envoy with an XDS server:
    ```bash
    envoy -c /path/to/xds-config.yaml --use-xds
    ```

---

### **Official Documentation Links**

1. **[Envoy Proxy Documentation](https://www.envoyproxy.io/docs/)**:  
   The official Envoy Proxy documentation provides comprehensive details about Envoy’s features, setup, configuration, and operational guides.

2. **[Getting Started with Envoy](https://www.envoyproxy.io/docs/envoy/latest/start/)**:  
   A beginner-friendly guide for getting started with Envoy in various environments.

3. **[Envoy Configuration Guide](https://www.envoyproxy.io/docs/envoy/latest/configuration/)**:  
   Detailed documentation on Envoy’s configuration syntax and all available configuration options.

4. **[Envoy CLI Reference](https://www.envoyproxy.io/docs/envoy/latest/operations/cli)**:  
   Complete list of commands and flags used to manage and interact with Envoy.

5. **[Envoy Filters Documentation](https://www.envoyproxy.io/docs/envoy/latest/configuration/http_filters/)**:  
   Learn how to extend Envoy’s functionality with HTTP filters for advanced routing, traffic management, and security features.

6. **[Envoy Admin API](https://www.envoyproxy.io/docs/envoy/latest/operations/admin/)**:  
   Reference for Envoy’s Admin API to manage, monitor, and configure Envoy proxies in production environments.
