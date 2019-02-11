# Apiomat Lurker Helm Chart

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
Name:                     apiomat-lurker
Namespace:                apiomat
Labels:                   app=apiomat-lurker
                          chart=apiomat-lurker-x.x.x
                          heritage=Tiller
                          release=apiomat-lurker
Selector:                 app=apiomat-lurker,release=apiomat-lurker
Type:                     NodePort
IP:                       172.24.26.192
Port:                     http  8090/TCP
TargetPort:               8090/TCP
NodePort:                 http  31176/TCP
Endpoints:                172.16.1.11:8090,172.16.7.44:8090
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
