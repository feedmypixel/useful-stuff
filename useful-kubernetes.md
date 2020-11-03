# Useful Kubernetes stuff

#### Cheatsheet
[kubectl/cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

#### Version
```
kubectl version
```

#### Get nodes
```
kubectl get nodes
```

#### get pods
```
kubectl get pods
```

#### get contexts
```
kubectl config get-contexts
```

#### set context
```
kubectl config set-context <context name> --cluster=<cluster> --namespace=<namespace> --user=<user email>
```

#### use context
```
kubectl config use-context <context name>
```

#### get context
```
kubectl config get-contexts
```

#### Get the rollout status
```
kubectl get rs
```

#### Delete ingress
```
kubectl delete -f production/k8s/ingress.yml 
```

#### Create ingress
```
kubectl create -f production/k8s/ingress.yml 
```

#### Apply ingress
```
kubectl apply -f production/k8s/ingress.yml 
```

#### Get ingress extensions
```
kubectl -n <namespace> get ingresses.extensions <namespace>-ingress-<environment>
```

#### Check events
```
kubectl -n <namespace> get events  --sort-by=.metadata.creationTimestamp
```

#### Edit deployment
Edit the file and then save - this will then apply the change and startup new pods
```
kubectl edit deployment
```
```
kubectl -n <namespace> edit deployment <namespace>-deployment-<environment>
```

#### Get Events
```
kubectl -n  <namespace>  get events
```

#### Exec in container
```
kubectl -n  <namespace> exec -ti <name> -- /bin/bash
```

#### Rollout history
```
kubectl -n <namespace> rollout history <namespace>-deployment-<environment>
```
e.g"
```
kubectl -n <namespace> rollout history deployment <namespace-deployment>
```

#### Stream logs
```
kubectl logs -f <name>
```

#### Decode secret
```
kubectl -n  <namespace> get secret <secret-name> -o json | jq -r '.data[] | @base64d'
```
