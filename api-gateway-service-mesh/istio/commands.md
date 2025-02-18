<img src="assets/image.png" alt="kong" width="250" >

## **Istio Commands**  

## **1. Installation & Setup**  

### **Download Istio CLI**  
```bash
curl -L https://istio.io/downloadIstio | sh -
cd istio-*
export PATH=$PWD/bin:$PATH
```

### **Install Istio in Kubernetes**  
```bash
istioctl install --set profile=demo -y
```

### **Verify Installation**  
```bash
istioctl verify-install
```

### **Enable Automatic Sidecar Injection for a Namespace**  
```bash
kubectl label namespace default istio-injection=enabled
```

### **Disable Sidecar Injection for a Namespace**  
```bash
kubectl label namespace default istio-injection-
```

---

## **2. Managing Istio Services**  

### **List All Istio Services**  
```bash
kubectl get svc -n istio-system
```

### **Get All Pods in Istio System**  
```bash
kubectl get pods -n istio-system
```

### **Get Istio Ingress Gateway**  
```bash
kubectl get svc istio-ingressgateway -n istio-system
```

### **Check Proxy Status for a Pod**  
```bash
istioctl proxy-status
```

---

## **3. Traffic Management**  

### **Apply Virtual Service**  
```bash
kubectl apply -f virtual-service.yaml
```

### **Apply Destination Rule**  
```bash
kubectl apply -f destination-rule.yaml
```

### **List Virtual Services**  
```bash
kubectl get virtualservices -A
```

### **List Destination Rules**  
```bash
kubectl get destinationrules -A
```

### **Delete a Virtual Service**  
```bash
kubectl delete virtualservice my-virtual-service
```

### **Delete a Destination Rule**  
```bash
kubectl delete destinationrule my-destination-rule
```

---

## **4. Monitoring & Logs**  

### **View Istio Logs for a Pod**  
```bash
kubectl logs <pod_name> -n istio-system
```

### **Check Istio Control Plane Status**  
```bash
kubectl get pods -n istio-system
```

### **Get Proxy Configuration for a Pod**  
```bash
istioctl proxy-config cluster <pod_name> -n <namespace>
```

### **View Traffic Routing Logs**  
```bash
kubectl logs -l istio=ingressgateway -n istio-system
```

---

## **5. Security & Policies**  

### **Apply Mutual TLS (mTLS) Policy**  
```bash
kubectl apply -f peer-authentication.yaml
```

### **List Authorization Policies**  
```bash
kubectl get authorizationpolicies -A
```

### **Delete an Authorization Policy**  
```bash
kubectl delete authorizationpolicy my-policy
```

### **Enable Strict mTLS for a Namespace**  
```bash
kubectl apply -f - <<EOF
apiVersion: security.istio.io/v1beta1
kind: PeerAuthentication
metadata:
  name: default
  namespace: default
spec:
  mtls:
    mode: STRICT
EOF
```

---

## **6. Istio Ingress Gateway Management**  

### **List Gateway Resources**  
```bash
kubectl get gateways -A
```

### **Delete a Gateway**  
```bash
kubectl delete gateway my-gateway
```

### **List Virtual Services Linked to Ingress**  
```bash
kubectl get virtualservice -n istio-system
```

---

## **7. Observability with Kiali, Grafana, and Jaeger**  

### **Get Kiali Dashboard URL**  
```bash
kubectl get svc kiali -n istio-system
```

### **Get Jaeger Tracing URL**  
```bash
kubectl get svc tracing -n istio-system
```

### **Open Grafana Dashboard**  
```bash
kubectl port-forward svc/grafana 3000:3000 -n istio-system
```

---

## **8. Uninstalling Istio**  

### **Remove Istio from Kubernetes**  
```bash
istioctl x uninstall --purge
```

### **Delete Istio Namespace**  
```bash
kubectl delete namespace istio-system
```

### **Remove Istio Label from Namespace**  
```bash
kubectl label namespace default istio-injection-
```

---

## **Documentation Links**  

- **Istio Official Docs** → [https://istio.io/latest/docs/](https://istio.io/latest/docs/)  
- **Istio Traffic Management** → [https://istio.io/latest/docs/tasks/traffic-management/](https://istio.io/latest/docs/tasks/traffic-management/)  
- **Istio Security** → [https://istio.io/latest/docs/tasks/security/](https://istio.io/latest/docs/tasks/security/)  
- **Istio Observability** → [https://istio.io/latest/docs/tasks/observability/](https://istio.io/latest/docs/tasks/observability/)  

---
