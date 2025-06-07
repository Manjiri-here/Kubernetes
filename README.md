Kubernetes
Docker is a platform for creating and running containers.
Kubernetes (K8s) is a container orchestration platform.
In simple words, Kubernetes manages and coordinates containers.

🟡 Why use Kubernetes instead of Docker?
Docker has some limitations that Kubernetes helps to solve:

1️⃣ Single Host Limitation
➡️ Docker runs containers on a single host (like one EC2 server).
➡️ Docker containers are ephemeral—they can die or restart at any time.
➡️ If one container uses too much memory, it affects other containers on the same host (because of how Linux works).

👉 How Kubernetes solves this:
Kubernetes uses a cluster (a group of servers).

The cluster has one master node and multiple worker nodes.

If a container is using too much memory and affecting others, Kubernetes moves the affected container to a different node.

This stops a single faulty container from harming the rest.

2️⃣ No Auto-Healing in Docker
➡️ If a container is stopped or killed, the application inside it is not accessible anymore.
➡️ A DevOps engineer must manually restart the container.

👉 How Kubernetes solves this:
Kubernetes has auto-healing.

When a container goes down, the API server notices and tells the system to start a new container automatically.

No manual work needed!

3️⃣ No Auto-Scaling in Docker
➡️ Imagine a streaming platform (like OTT) using Docker.
➡️ If many users join and CPU/RAM are fully used, you need more containers to handle the load.
➡️ Docker doesn’t have built-in auto-scaling.
➡️ You’d have to manually create new containers and set up a load balancer.

👉 How Kubernetes solves this:
Kubernetes can auto-scale using:

ReplicaSet: You define in a YAML file how many replicas (containers) you need.

HPA (Horizontal Pod Autoscaler): You set rules (like “if CPU usage is over 80%, add more containers”).

This way, Kubernetes automatically adds new containers when needed.

4️⃣ No Enterprise-Level Support in Docker
➡️ Docker is simple and minimal, so it lacks many enterprise features.
➡️ Without tools like Docker Swarm or Kubernetes, Docker does not support:

Load balancers

Firewalls

Auto-scaling

Auto-healing

API gateways

👉 How Kubernetes solves this:
Kubernetes provides enterprise-grade support for these features.
It’s always improving to meet security and functionality standards.

🌟 A Bit of History
Kubernetes was created at Google when they worked on a tool called Borg.

Today, it’s managed by the CNCF (Cloud Native Computing Foundation), an open-source community that also helps improve K8s and related tools.

For example, Kubernetes doesn’t have advanced load balancing on its own (it only supports basic round-robin balancing).

So, Kubernetes allows apps like NGINX and HAProxy to create their own load balancers (via custom resources and custom controllers).

That’s how the Ingress load balancer was introduced!
