## Kubernetes Components

### References
- https://roadmap.sh/kubernetes

---
### 1. **Service**
- Provides a **permanent static IP address**
- Acts as a **load balancer**
- Used to **expose** pods internally or externally

### 2. **Ingress**
- Binds an **IP address** to a **domain name**
- Manages external access to services (typically HTTP)

### 3. **ConfigMap**
- Stores **external configurations**
- Keeps configurations **separate from code**

### 4. **Secrets**
- Stores **sensitive data** like:
  - Credentials
  - Certificates
- Data is **base64 encoded**

### 5. **Volumes**
- Provide **persistent storage**
- Useful for stateful applications that require disk space beyond pod lifecycle

---

## StatefulSet

- Used for **stateful applications** (e.g., databases)
- Ensures **stable pod identity and storage**
- Maintains **consistency** across **concurrent transactions**

---

## Node Components

### Kubelet
- Interface between **container runtime** and **node**
- Responsible for:
  - Running containers
  - Registering the node with the cluster
  - Monitoring pod status

### Kube Proxy
- Handles **network routing**
- Forwards requests to the correct pod (even across nodes)
- Maintains network rules on nodes

### Container Runtime
- The underlying software to run containers (e.g., **containerd**, **Docker**, **CRI-O**)

---

## Master Node Components

### API Server
- Central access point for the Kubernetes control plane
- Receives and processes REST operations

### Scheduler
- Assigns newly created pods to nodes
- Acts like a **load balancer** for pods

### Controller Manager
- Monitors the cluster
- Makes changes to bring the current state to the **desired state**

### etcd
- **Key-value store**
- Acts as the **cluster brain**
- Stores all cluster data (state, configs, secrets)

---

