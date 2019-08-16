# Useful Azure Stuff

#### Login
```
az login
```

#### show log
```
az webapp log show -n <webapp-name> -g <resource-group>
```
###### example:

```
az webapp log show -n fesk-pdp-stage -g fesk-pdp
```

#### Login to kubernetes
```
az aks get-credentials -g shared -n dev
```


#### List account
```
az account list -o table
```

#### Set default account
```
az account set -s <SubscriptionId>
```