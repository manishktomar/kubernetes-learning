# Workloads & Controllers
1. Deployments: 
2. Replica Sets: 
3. Daemon Sets: 
4. Jobs: 
5. CronJobs: 
6. Horizontal Pod Autoscaler:

## Deployments: 
Purpose: Deployments are used to manage stateless applications and ensure that the desired number of pod replicas are running. They provide rolling updates and rollback capabilities.
Key Points:

- Replicas: Number of pod replicas.
- Rolling Updates: Manage updates without downtime.
- Rollback: Revert to a previous state if an update fails.
```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
    name: my-deployment
    spec:
    replicas: 3
    selector:
        matchLabels:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: my-registry/my-app:latest
            ports:
            - containerPort: 80
```
```
    kubectl get deployments
    kubectl describe deployment <deployment-name>
```
## Replica Sets: 
Purpose: Ensures a specified number of pod replicas are running at any given time. Typically managed by a Deployment.

- Selector: Defines which pods to manage.
- Managed by Deployments: Generally not created directly.
```
    apiVersion: apps/v1
    kind: ReplicaSet
    metadata:
    name: my-replicaset
    spec:
    replicas: 3
    selector:
        matchLabels:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: my-registry/my-app:latest
            ports:
            - containerPort: 80
```
```
kubectl get replicasets
kubectl describe replicaset <replicaset-name>
```

## Replica Controller:
Purpose: Similar to Replica Sets but older and less preferred. Ensures a specified number of pod replicas are running.

- Selector: Defines which pods to manage.
- Deprecated: Use Replica Sets and Deployments instead.
```
    apiVersion: v1
    kind: ReplicationController
    metadata:
    name: my-replicationcontroller
    spec:
    replicas: 3
    selector:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: my-registry/my-app:latest
            ports:
            - containerPort: 80
```
```
    kubectl get replicationcontrollers
    kubectl describe replicationcontroller <replicationcontroller-name>
```

## StatefulSets: 
Purpose: Manage stateful applications that require stable, unique network identifiers and persistent storage.

- Stable Network Identity: Each pod gets a unique name.
- Persistent Storage: Manages persistent volume claims.
```
    apiVersion: apps/v1
    kind: StatefulSet
    metadata:
    name: my-statefulset
    spec:
    serviceName: "my-service"
    replicas: 3
    selector:
        matchLabels:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: my-registry/my-app:latest
            ports:
            - containerPort: 80
    volumeClaimTemplates:
    - metadata:
        name: my-persistent-volume-claim
        spec:
        accessModes: ["ReadWriteOnce"]
        resources:
            requests:
            storage: 1Gi
```
```
    kubectl get statefulsets
    kubectl describe statefulset <statefulset-name>
```
## Daemon Sets: 
Purpose: Ensure that a copy of a pod runs on all (or some) nodes. Useful for logging, monitoring, and system maintenance tasks.

- Node Coverage: Ensures pods are scheduled on every node.
- Useful for System Pods: e.g., log collection, monitoring.
```
    apiVersion: apps/v1
    kind: DaemonSet
    metadata:
    name: my-daemonset
    spec:
    selector:
        matchLabels:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: my-registry/my-app:latest
            ports:
            - containerPort: 80
```
```
    kubectl get daemonsets
    kubectl describe daemonset <daemonset-name>
```

## Jobs: 
Purpose: Run a batch or one-time job that creates one or more pods and ensures they complete successfully.

- One-time Execution: Useful for tasks that need to run to completion.
- Retries: Configurable to retry on failure.
```
    apiVersion: batch/v1
    kind: Job
    metadata:
    name: my-job
    spec:
    template:
        spec:
        containers:
        - name: my-container
            image: my-registry/my-job:latest
            command: ["sh", "-c", "echo Hello Kubernetes!"]
        restartPolicy: OnFailure
```
```
kubectl get jobs
kubectl describe job <job-name>
```

## CronJobs: 
Purpose: Run Jobs on a scheduled basis, similar to cron jobs in Unix-based systems.

- Scheduled Jobs: Runs jobs periodically.
- Cron Schedule Syntax: Uses cron syntax to specify timing.
```
    apiVersion: batch/v1
    kind: CronJob
    metadata:
    name: my-cronjob
    spec:
    schedule: "0 0 * * *"  # Runs daily at midnight
    jobTemplate:
        spec:
        template:
            spec:
            containers:
            - name: my-container
                image: my-registry/my-job:latest
                command: ["sh", "-c", "echo Hello Kubernetes!"]
            restartPolicy: OnFailure
```
```
    kubectl get cronjobs
    kubectl describe cronjob <cronjob-name>
```
## Horizontal Pod Autoscaler:
Purpose: Automatically scales the number of pod replicas based on CPU utilization or other select metrics.

- Autoscaling: Adjusts the number of replicas based on CPU usage or custom metrics.
- Min and Max Replicas: Defines the scaling range.
```
    apiVersion: autoscaling/v1
    kind: HorizontalPodAutoscaler
    metadata:
    name: my-hpa
    spec:
    scaleTargetRef:
        apiVersion: apps/v1
        kind: Deployment
        name: my-deployment
    minReplicas: 1
    maxReplicas: 10
    targetCPUUtilizationPercentage: 80
```
```
    kubectl get hpa
    kubectl describe hpa <hpa-name>
```
