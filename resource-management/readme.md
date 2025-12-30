# 3. Resource Management: Practice managing Kubernetes resources like Pods, Services, and Deployments?
I practiced various commands to manage the resources from the previous deployment.

## Steps 
- Lists pods:
```text
kubectl get pods
```
Output:
```text
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-66b6c48dd5-abcde   1/1     Running   0          5m
nginx-deployment-66b6c48dd5-fghij   1/1     Running   0          5m
```

- Describe a Pod:
```text
kubectl describe pod <pod_name>
```
This showed details like events, conditions, and container status.

- Lists Services: 
```text
kubectl get services
```
Output: 
```text
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
kubernetes      ClusterIP      10.96.0.1       <none>        443/TCP        10m
nginx-service   LoadBalancer   10.111.222.333  <pending>     80:30300/TCP   5m
```

- Scale the deployment:
```text
kubectl scale deployment nginx-deployment --replicas=3
``` 
Then check the deployment,
```text
kubectl get deployments
``` 
It showed 3/3 ready.

- Delete the pod:
```text
kubectl delete pod <pod_name>
```
The deployment automatically created a new one.

- View logs:
```text
kubectl logs <pod_name>
```
These commands helped me understand how to monitor and manage resources.
    