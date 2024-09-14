# Kubernetes Services Networking
| Concept | Description |
| --- | --- |
| [Services](#Services) |	Expose a set of pods and make them discoverable within the cluster or to external clients. |
| [Ingress](#Ingress) |	Manage external access to services, typically HTTP(S) traffic, with routing, SSL, and load balancing. |
| [Network Policies](#network-policies) | Define rules for allowing/restricting network communication between pods at the IP/port level. |
| [Service Discovery](#Service-Discovery) |Automatic mechanism to discover services via DNS or environment variables. |
| [Load Balancer](#load-balancer) |Provides an external load balancer to route traffic to services from outside the cluster. |

## 1. Services: 
A Service in Kubernetes is an abstraction that defines a logical set of pods and a policy by which to access them. Services enable communication between different parts of your application and between your application and external users.

Types of Services:
- **ClusterIP (default)**: Exposes the service on a cluster-internal IP. Pods inside the cluster can communicate with the service.
- **NodePort**: Exposes the service on each Node's IP at a static port. External traffic can access it using <NodeIP>:<NodePort>.
- **LoadBalancer**: Exposes the service externally using a cloud provider's load balancer. It automatically provisions the load balancer for services.
- **ExternalName**: Maps the service to a DNS name.
```
    apiVersion: v1
    kind: Service
    metadata:
    name: my-service
    spec:
    selector:
        app: my-app
    ports:
        - protocol: TCP
        port: 80
        targetPort: 8080
    type: LoadBalancer
```

## 2. Ingress: 
Ingress is an API object that manages external access to services, typically HTTP. It provides load balancing, SSL termination, and name-based virtual hosting.

- **Ingress Controller**: You need an ingress controller to implement the rules defined in the Ingress resource. Common ones include NGINX, Traefik, and HAProxy.
- **Routing**: Ingress allows for HTTP/HTTPS routing based on URL paths or hostnames, directing traffic to specific services.
```
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
    name: example-ingress
    spec:
    rules:
    - host: example.com
        http:
        paths:
        - path: /
            pathType: Prefix
            backend:
            service:
                name: my-service
                port:
                number: 80
```

## 3. Network Policies: 
Network Policies control the communication between pods within a Kubernetes cluster. By default, Kubernetes allows all communication between pods, but network policies restrict that behavior, defining which pods can communicate with each other.

- **Pod Selector**: Network policies apply to a set of pods selected by a label.
- **Ingress and Egress**: Define rules for both incoming (ingress) and outgoing (egress) traffic for the selected pods.
- **Layer 3/4 Control**: Network policies operate at layer 3 (IP) and layer 4 (TCP/UDP port).
```
    apiVersion: networking.k8s.io/v1
    kind: NetworkPolicy
    metadata:
    name: allow-ingress
    spec:
    podSelector:
        matchLabels:
        app: my-app
    policyTypes:
    - Ingress
    ingress:
    - from:
        - podSelector:
            matchLabels:
            role: frontend
        ports:
        - protocol: TCP
        port: 80
```

## 4. Service Discovery: 
Service Discovery is how Kubernetes applications discover services within the cluster. It happens automatically, and there are two primary mechanisms:

- **DNS-based Service Discovery**: When a service is created, Kubernetes adds a DNS entry so that any pod in the cluster can discover the service by its name (e.g., my-service.namespace.svc.cluster.local).
- **Environment Variables**: Kubernetes injects environment variables into pods with the service's information (IP, port).

Kubernetes' internal DNS system resolves service names to their corresponding cluster IPs.

## 5. Load Balancer: 
A LoadBalancer service type in Kubernetes allows external traffic to access services via an external load balancer provided by the underlying cloud provider (e.g., AWS, GCP, Azure). The load balancer automatically forwards traffic to the appropriate pods.

- **Cloud Provider Integration**: Kubernetes automatically provisions the external load balancer through the cloud provider's API.
- **External Access**: LoadBalancers provide an external IP or hostname, making the service accessible from the internet.
```
    apiVersion: v1
    kind: Service
    metadata:
    name: my-loadbalancer-service
    spec:
    selector:
        app: my-app
    ports:
        - protocol: TCP
        port: 80
        targetPort: 8080
    type: LoadBalancer
```
