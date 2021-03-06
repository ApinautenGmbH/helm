# Apiomat Explorer Helm Chart

## Install

```bash
helm install --name <deployment_name> ./ --set service.type=NodePort
```

## Expose

```bash
kubectl expose deployment <deployment_name> --type=LoadBalancer --name=<service_name>
```

## Check Service and get External Endpoint

```bash
kubectl describe service <service_name>
```

Shoud return something similar to:
```bash
Name:                     apiomat-explorer
Namespace:                apiomat
Labels:                   app=apiomat-explorer
                          chart=apiomat-explorer-x.x.x
                          heritage=Tiller
                          release=apiomat-explorer
Selector:                 app=apiomat-explorer,release=apiomat-explorer
Type:                     NodePort
IP:                       172.24.26.192
Port:                     http  8094/TCP
TargetPort:               8094/TCP
NodePort:                 http  31176/TCP
Endpoints:                172.16.1.11:8094,172.16.7.44:8094
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
