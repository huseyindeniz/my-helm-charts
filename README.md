## Notes

### Argo CD Installation into Kubernetes using HELM

```bash
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/
helm install argo-cd charts/argo-cd/
```

**Port forwarding**

```bash
kubectl port-forward svc/argo-cd-argocd-server 8080:443
```

**Get Password**

```bash
kubectl get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
