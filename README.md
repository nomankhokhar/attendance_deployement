# **Kubernetes Deployment for Frontend, Backend, and MongoDB**

This repository contains Kubernetes manifests to deploy a **frontend, backend, and MongoDB database** on a Kubernetes cluster.

## **Project Overview**
The system consists of:
- **Frontend**: A static website served using **Nginx**.
- **Backend**: A **Go** application handling API requests.
- **MongoDB**: A **MongoDB** database for storing data.

## **Kubernetes Components**
Each component is deployed using **Deployments** and exposed using **Services**.

| Service  | Type         | Port | Image |
|----------|-------------|------|-------------------|
| Frontend | ClusterIP   | 80   | `nomanali1114/frontend` |
| Backend  | ClusterIP   | 8080 | `nomanali1114/backend` |
| MongoDB  | ClusterIP   | 27017 | `mongo:6.0` |

---

## **Setup & Deployment**
### **Prerequisites**
Ensure you have the following installed:
- [Docker](https://www.docker.com/)
- [Kubernetes (kubectl)](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/) (for local testing)

### **Deploy the Services**
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/kubernetes-deployment.git
   cd kubernetes-deployment
   ```

2. Apply the Kubernetes YAML files:
   ```sh
   kubectl apply -f frontend.yaml
   kubectl apply -f backend.yaml
   kubectl apply -f mongodb.yaml
   ```

3. Verify deployment:
   ```sh
   kubectl get pods
   kubectl get services
   ```

### **Accessing the Services**
- **Frontend**: Expose via `NodePort` or port-forward:
  ```sh
  kubectl port-forward service/frontend-service 8080:80
  ```
  Access via `http://localhost:8080`.

- **Backend**: Expose via:
  ```sh
  kubectl port-forward service/backend-service 8081:8080
  ```
  Access via `http://localhost:8081`.

---

## **Cleaning Up**
To remove the deployment:
```sh
kubectl delete -f frontend.yaml
kubectl delete -f backend.yaml
kubectl delete -f mongodb.yaml
```

---

## **Future Improvements**
- Add **Ingress Controller** for better service management.
- Implement **Horizontal Pod Autoscaling**.
- Use **Persistent Volumes** for MongoDB in production.

---

### **Author**
👤 @nomankhokhar   
