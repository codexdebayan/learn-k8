## Kubernetes Components - _Learn with codexdebayan_

### References
- [Roadmap.sh](https://roadmap.sh/kubernetes)
- [YouTube](https://youtu.be/X48VuDVv0do?si=0Wlax-stebzTjFqT&t=2991)

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

## Mandatory Node Components

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

## How to setup localy
|Steps| Required Items | Links|
|:--|:------------- |:-----|
|1| `Minikube` | [Download](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download) |
|2| `kubectl` | [Download](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/#install-kubectl-binary-on-windows-via-direct-download-or-curl)|
|3| `VirtualBox` | [Download](https://www.virtualbox.org/)|

>** **Note:** You might requrie `windows c++ redistributable 2019`, [Dowload](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-supported-redistributable-version) both x86 and x64 architecture if windows.
>
>** `Virtualization not enabled from BIOS`: If such error pops up even after enabling it then try `minikube start --no-vtx-check` instead of `minikube start`

## Steps to start a K8 container (local)

### Using Docker and minikube

```
minikube start --driver=docker --kubernetes-version=v1.29.4

kubectl get nodes

```

### Using Docker and Kind
```
curl.exe -Lo kind.exe https://kind.sigs.k8s.io/dl/v0.22.0/kind-windows-amd64

mkdir C:\kind
move kind.exe C:\kind\

setx PATH "$env:PATH;C:\kind"

kind version

kind create cluster

kubectl get nodes
```

## kubectl commands

```
kubectl version
kubectl get nodes
kubectl get pods
kubectl get services
kubectl get replicaset 

--- deployment ---
kubectl create deployment nginx-depl --image=nginx

```
>![Comparison between the naming of Deployment, Replicaset & Pod](/assets/deployment-replicaset-pod.png)
>Fig : 1.1 Comparison between the naming of Deployment, Replicaset & Pod

## Replicaset
 Managing the replicas of a pod