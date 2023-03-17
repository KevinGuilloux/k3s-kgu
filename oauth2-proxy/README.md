Créer le fichier suivant ./oauth2-proxy/templates/secret.yaml

```
apiVersion: v1
kind: Secret
metadata:
  name: oauth2-proxy-secret
  annotations:
    sealedsecrets.bitnami.com/cluster-wide: "true"
data:
  client-id: <echo -n "b9d26f4337b3e40a5376" | base64>
  client-secret: <echo -n "725e6e850117dbff3e911d9050c8e5e01d2efda0" | base64>
  cookie-secret: <openssl rand -base64 32 | head -c 32 | base64>
```

```
  kubeseal -f ./oauth2-proxy/templates/secret.yaml --format yaml > ./oauth2-proxy/templates/secret-sealed.yaml
```

```
 kubectl apply -f ./oauth2-proxy/templates/secret-sealed.yaml
```
