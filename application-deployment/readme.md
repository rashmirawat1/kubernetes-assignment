# 2. Application Deployment: Deploy a simple application to your Kubernetes cluster?
For a simple application, I deployed an NGINX web server using a Deployment.

## Steps
- Create a deployment YAML file named nginx-deployment.yaml:
    
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

- Apply the deployment: 
```text
kubectl apply -f nginx-deployment.yaml
```
Output:

deployment.apps/nginx-deployment created


- Check the deployment:
```text
kubectl get deployments
``` 
Output:

NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   2/2     2            2           1m


- To access it, create a Service YAML nginx-service.yaml:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: LoadBalancer
```

- Apply:
```text
kubectl apply -f nginx-service.yaml
```  

- Get the URL:
```text
minikube service nginx-service --url
```   

This gave me a local URL, and opening it showed the NGINX welcome page.

![Image](/application-deployment/nginxpage.png)
    
    