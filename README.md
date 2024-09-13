# ![Kubernetes](https://skillicons.dev/icons?i=kubernetes) Kubernetes Learing
![k8](https://github.com/user-attachments/assets/531203b0-9145-4079-b4b8-20cdc71fd92f)

1. Kubernetes Installation  [Document](./Deployment.md)
2. Service 
3. Deployment 
4. Replica Set and Replica Controller
5. Namespace
4. Manifest Example



### 1. Workloads & Controllers

| Command | Description |
| --- | --- |
| git status | List all new or modified files |
| git diff | Show file differences that haven't been staged |
| Deployments:  | Manages a replicated application. | 
| Replica Sets:  | Ensures that a specified number of replicas of a Pod are running at all times. | 
| Replica Controller: |  | 
| Stateful Sets: |  Manages the deployment and scaling of a set of Pods, providing guarantees about ordering and uniqueness. | 
| Daemon Sets: |  Ensures that all (or some) nodes run a copy of a Pod. | 
| Jobs: |  Creates one or more Pods and ensures that a specified number of them successfully terminate. | 
| CronJobs: |  Manages time-based Jobs, such as running a Job at a specific time or periodic intervals. | 
| Horizontal Pod Autoscaler: |  Automatically scales the number of Pods in a deployment, replica set, or replication controller based on observed CPU or memory usage. | 

- **Deployments:** 	Manages a replicated application.
- **Replica Sets:** 	Ensures that a specified number of replicas of a Pod are running at all times.
- **Replica Controller:** 	
- **Stateful Sets:** 	Manages the deployment and scaling of a set of Pods, providing guarantees about ordering and uniqueness.
- **Daemon Sets:** 	Ensures that all (or some) nodes run a copy of a Pod.
- **Jobs:** 	Creates one or more Pods and ensures that a specified number of them successfully terminate.
- **CronJobs:** 	Manages time-based Jobs, such as running a Job at a specific time or periodic intervals.
- **Horizontal Pod Autoscaler:**	Automatically scales the number of Pods in a deployment, replica set, or replication controller based on observed CPU or memory usage.

### 2. Services & Networking:

- **Services:** 	A way to expose an application running in Pods as a network service.
- **Ingress:** 	Manages external access to services within a cluster.
- **Network Policies:** 	Define how Pods communicate with each other.
- **Service Discovery:** 	Mechanism to connect to services dynamically based on a logical name.
- **Load Balancer:** 	A service that distributes network traffic across multiple Pods.

### 3. Kubernetes Storage:

- **Persistent Volumes (PVs):**	Offers storage to the cluster that is independent of Pod life cycles.
- **Storage Classes:**	Allow administrators to describe the "classes" of storage offered.

### 4. Configuration & Secrets: 

- **ConfigMaps:**	Manage configuration data separately from container images.
- **Secrets:**	Manages sensitive information, such as passwords, OAuth tokens, and ssh keys.
- **Environment Variables:**	Used within Kubernetes for service discovery.

### 5. Kubernetes Automation and Autoscaling

- **Cluster Autoscaler:** Automatically adjusts the size of the cluster, scaling it up or down as necessary.
- **Vertical Pod Autoscaler:** Automatically adjusts the amount of CPU and memory requested by containers in a Pod.
- **Horizontal Pod Autoscaler (HPA):** Automatically scales the number of Pods in a deployment or replica set based on observed CPU or memory utilization.
