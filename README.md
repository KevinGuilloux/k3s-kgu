# k3s-kgu

S'assurer que helm dispose de la configuration de kubernetes pour effectuer des actions dessus :

```
kubectl config view --raw > ~/.kube/config
```

```
cd ./argocd/argocd/
helm dependency build
cd ../..
cd ./argocd/argocd-apps/
helm dependency build
cd ../..



helm install argocd ./argocd/argocd --namespace argocd --create-namespace
helm install argocd-apps ./argocd/argocd-apps --namespace argocd


https://argo-cd.k3s-kgu.gnc.recif.nc/
user : admin
password : `kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d && echo`


kubectl create secret generic mysecret --dry-run=client  -o yaml --from-literal=password=azerty123 > mysecret.yaml
kubeseal -f mysecret.yaml --format yaml > mysealedsecret.yaml
```
