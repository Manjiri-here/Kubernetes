# Kubernetes Architecture

Kubernetes has two main planes:

✅ **Control Plane (or Master Plane)**  
This plane contains these components:
1. **API Server**
2. **ETCD**
3. **Scheduler**
4. **Controller Manager**
5. **Cloud Controller Manager**

✅ **Data Plane**  
This plane contains these components:
1. **Kubelet**
2. **Proxy**
3. **Container Runtime**

# Kubernetes Data and Control Plane Components

---
## 🔷 Data plane/worker node components

✅ **Container Runtime**

In Docker, you have a server. You install Docker there and run a container. But it will not run unless you have a component called **Docker shim**.

Similarly, in Kubernetes, the **Container Runtime** is the essential component.  
It’s required to run the container.

Think of it like this:  
- Java needs the **Java Runtime** to run Java applications.  
- Kubernetes needs the **Container Runtime** to run containers.

✅ **Kubelet**  
- Responsible for maintaining the **Pod** and ensuring it is running.  
- Kubelet reports if something goes wrong with the Pod.

✅ **kube-proxy**  
- In Docker, networking is handled by `docker0` or bridge networking.  
- In Kubernetes, networking is managed by **kube-proxy**.  
- It provides networking, assigns IP addresses, and basic load balancing.  
- It uses **ip-tables** on Linux.

# 🔷 Why is the Control Plane (Master Node) Needed?

The Control Plane manages the entire Kubernetes cluster.  
It defines **standard policies**, like deciding on which node a Pod should be created.

---

## 🔷 Control Plane Components

✅ **API Server**  
- The core component and the “**heart** of Kubernetes.  
- I exposes Kubernetes APIs to the outside world.  
- For example, when a user tries to create a Pod, they access the API Server.  
- The API Server decides: “Node 1 is free; the Pod can be created there.”

✅ **Scheduler**  
- The **API Server** decides which node is free.  
- The **Scheduler** actually schedules the Pod on that node.  
- So: API Server makes the decision; Scheduler acts on it.

✅ **etcd**  
- The **backing store** for all Kubernetes data.  
- A **key-value store** that stores configuration and state.

✅ **Controller Manager**  
- Kubernetes supports **auto-scaling** (like ReplicaSets to maintain the desired number of Pods).  
- The Controller Manager ensures these **controllers** are always running.

✅ **Cloud Controller Manager (CCM)**  
- Kubernetes can run on cloud platforms like **EKS** or **AKS**.  
- For example, if there’s a request to create a cloud load balancer, the CCM translates it for the cloud provider.  
- CCM is an **open-source** utility (it has a GitHub repo).  
- You can write custom code for your cloud provider.  
- **Not needed** for on-premise Kubernetes; only used when running on cloud.
