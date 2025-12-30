# 4. Helm Charts: Use Helm to package and deploy applications on Kubernetes?
Helm is like a package manager for Kubernetes. I used it to deploy a sample chart.

## Steps 
- Install Helm:
```text
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

- Add Repo:
```text
helm repo add bitnami https://charts.bitnami.com/bitnamihelm repo update
```

- Install: 
```text
helm install my-apache bitnami/apache
```
Output: 
```text
NAME: my-apache
LAST DEPLOYED: Tue Dec 30 2025 10:00:00
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

- List:
```text
helm list
``` 
Output: 
```text
NAME       NAMESPACE REVISION UPDATED                                 STATUS   CHART         APP VERSION
my-apache  default   1        2025-12-30 10:00:00.000000000 +0000 UTC deployed apache-11.0.0 2.4.62     
```

- Upgrade:
```text
helm upgrade my-apache bitnami/apache --set replicaCount=2
```

- Unistall:
```text
helm uninstall my-apache
```
This deployed the Apache server with pods and services automatically.
    