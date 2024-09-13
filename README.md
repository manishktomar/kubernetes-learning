# ![Kubernetes](https://skillicons.dev/icons?i=kubernetes) Kubernetes Learing
![image](https://github.com/user-attachments/assets/c387068f-5bbf-4e1a-b696-484d3db4ee2c)


1. Kubernetes Installation  [Document](./Deployment.md)
2. Service 
3. Deployment 
4. Replica Set and Replica Controller
5. Namespace
4. Manifest Example


### 1. Workloads & Controllers

| Command | Description |
| --- | --- |
| Deployments:  | Deployments are used to manage stateless applications and ensure that the desired number of pod replicas are running. They provide rolling updates and rollback capabilities. | 
| Replica Sets:  | Ensures a specified number of pod replicas are running at any given time. Typically managed by a Deployment. | 
| Replica Controller: | Similar to Replica Sets but older and less preferred. Ensures a specified number of pod replicas are running. | 
| Stateful Sets: |  Manages the deployment and scaling of a set of Pods, providing guarantees about ordering and uniqueness. | 
| Daemon Sets: |  Ensures that all (or some) nodes run a copy of a Pod. | 
| Jobs: |  Creates one or more Pods and ensures that a specified number of them successfully terminate. | 
| CronJobs: |  Manages time-based Jobs, such as running a Job at a specific time or periodic intervals. | 
| Horizontal Pod Autoscaler: |  Automatically scales the number of Pods in a deployment, replica set, or replication controller based on observed CPU or memory usage. | 

### 2. Services & Networking:

| Command | Description |
| --- | --- |
| Services:|  A way to expose an application running in Pods as a network service.| 
| Ingress:|  Manages external access to services within a cluster.| 
| Network Policies:|  Define how Pods communicate with each other.| 
| Service Discovery:|  Mechanism to connect to services dynamically based on a logical name.| 
| Load Balancer:|  A service that distributes network traffic across multiple Pods.| 

### 3. Kubernetes Storage:

| Command | Description |
| --- | --- |
| Persistent Volumes (PVs):|  Offers storage to the cluster that is independent of Pod life cycles.| 
| Storage Classes:|  Allow administrators to describe the "classes" of storage offered.| 

### 4. Configuration & Secrets: 

| Command | Description |
| --- | --- |
| ConfigMaps:|  Manage configuration data separately from container images.| 
| Secrets:|  Manages sensitive information, such as passwords, OAuth tokens, and ssh keys.| 
| Environment Variables:|  Used within Kubernetes for service discovery.| 

### 5. Kubernetes Automation and Autoscaling

| Command | Description |
| --- | --- |
| Cluster Autoscaler:|  Automatically adjusts the size of the cluster, scaling it up or down as necessary.| 
| Vertical Pod Autoscaler:|  Automatically adjusts the amount of CPU and memory requested by containers in a Pod.| 
| Horizontal Pod Autoscaler (HPA):|  Automatically scales the number of Pods in a deployment or replica set based on observed CPU or memory utilization.| 
