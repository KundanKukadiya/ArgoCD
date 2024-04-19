# ArgoCD
ArgoCD is GitOps continues delivery tool for Kubernetes

### Why Argo CD
1. Application definitions, configurations, and environments should be declarative and version controlled. Application deployment and lifecycle management should be automated, auditable, and easy to understand.
2. Argo CD API/Web is the only component that we need to interact with to manage applications.

### Architecture :
<img src = "https://github.com/KundanKukadiya/ArgoCD/assets/41021278/04008bf9-30a4-4222-891d-7c3c586ab885" width="450" height="300">

### Installation Steps:
```
# This will create a new namespace, argocd, where Argo CD services and application resources will live.
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
### Access The Argo CD API Server
1. Service Type Load Balancer
   - Change the argocd-server service type to LoadBalancer: <br>
    ``` kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}' ```
2. Ingress
   - Follow the ingress documentation on how to configure Argo CD with ingress.
3. Port Forwarding
   - Kubectl port-forwarding can also be used to connect to the API server without exposing the service. <br>
     ``` kubectl port-forward svc/argocd-server -n argocd 8080:443 ```

