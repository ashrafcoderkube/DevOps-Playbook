<img src="assets/image.png" alt="envoy" width="250" >

Here is a list of common commands used with Envoy Proxy:

### **Envoy Command-Line Interface (CLI)**

1. **Start Envoy with a Configuration File:**
   This command starts Envoy with a specified YAML configuration file.
   ```bash
   envoy -c /path/to/envoy.yaml
   ```

2. **Start Envoy with Debug Logging:**
   To run Envoy in debug mode for troubleshooting.
   ```bash
   envoy -c /path/to/envoy.yaml --log-level debug
   ```

3. **Check Envoy Version:**
   This command checks the current version of Envoy that is installed.
   ```bash
   envoy --version
   ```

4. **Start Envoy with a Specific Service Cluster Configuration:**
   Run Envoy to proxy requests based on a specific service cluster.
   ```bash
   envoy -c /path/to/service-cluster-config.yaml
   ```

5. **View Envoy Stats (via HTTP API):**
   Envoy exposes internal metrics through the `/stats` endpoint. You can view them using a `curl` command:
   ```bash
   curl http://localhost:8001/stats
   ```

6. **View Envoy Configuration (via Admin API):**
   The `/config_dump` endpoint provides the full configuration dump of the running Envoy proxy.
   ```bash
   curl http://localhost:8001/config_dump
   ```

7. **Check the Status of Envoy (via Admin API):**
   To check the status of the Envoy proxy, you can use the `/server_info` endpoint.
   ```bash
   curl http://localhost:8001/server_info
   ```

8. **Reload Envoy Configuration Without Restarting:**
   To apply a configuration change without restarting Envoy, send a `SIGHUP` signal to the Envoy process.
   ```bash
   kill -SIGHUP <envoy_pid>
   ```

9. **Start Envoy with TLS Termination:**
   If Envoy is handling TLS termination, you would use a TLS configuration file:
   ```bash
   envoy -c /path/to/envoy-tls-config.yaml
   ```

10. **Run Envoy with XDS (Extensible Data Plane API):**
    Envoy can be integrated with a control plane using XDS to fetch configuration dynamically.
    ```bash
    envoy -c /path/to/xds-config.yaml --use-xds
    ```

11. **List Active Listeners in Envoy:**
    The following command lists the active listeners in Envoy.
    ```bash
    curl http://localhost:8001/listeners
    ```

12. **View Health Check Status:**
    Envoy allows you to configure health checks for backends. You can view the health check status using this command.
    ```bash
    curl http://localhost:8001/healthcheck
    ```

13. **Envoy Admin – Drain the Server:**
    To gracefully shut down a server and drain connections.
    ```bash
    curl -X POST http://localhost:8001/quitquitquit
    ```

14. **Check Running Envoy Instance:**
    To check if Envoy is running, you can use the `ps` or similar command to verify its process.
    ```bash
    ps aux | grep envoy
    ```

---

### **Additional Useful Envoy Commands for Troubleshooting**

- **Check Envoy's Active Routes:**
   You can query Envoy for active routes via its admin API.
   ```bash
   curl http://localhost:8001/routes
   ```

- **Checking Server Metrics with Prometheus Endpoint:**
   If you have Prometheus set up for monitoring, you can fetch Envoy metrics using the Prometheus endpoint.
   ```bash
   curl http://localhost:8001/prometheus
   ```

- **Admin API for Envoy:**
   Envoy's Admin API can provide various other diagnostics such as logs, stats, listeners, and cluster information.
   - List of admin commands:  
     ```bash
     curl http://localhost:8001/command_line
     ```

These are some of the key commands that you would typically use when configuring, running, and troubleshooting Envoy Proxy. Make sure to adjust the paths (like `/path/to/envoy.yaml`) and ports (`localhost:8001`) to match your setup.