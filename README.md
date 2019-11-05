# argocd

Cache origin manifest locally

```sh
kustomize build origin > origin.yaml
```

Install to cluster

```sh
kubectl apply -k .
```

Login cluster

```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
argocd login localhost:8080 --name flax.local --username admin --password `kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2`
```
