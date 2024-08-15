# Setting up Argo CD with Helm

## Notes

### Argo CD First Installation into Kubernetes using HELM

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

### Argo CD manage itself

charts/root-app/templates/argo-cd.yaml

### Root-App notes

This app will renders Application manifests we add later

add it to argocd first time

```bash
helm template ./charts/root-app/ | kubectl apply -f -
```

## References

- [setting-up-argocd-with-helm/](https://www.arthurkoziel.com/setting-up-argocd-with-helm/)
