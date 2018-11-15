# Apiomat Yambas Helm Chart

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
Name:                     apiomat-yambas
Namespace:                apiomat
Labels:                   app=apiomat-yambas
                          chart=apiomat-yambas-0.2.1
                          heritage=Tiller
                          release=apiomat-dashboard
Selector:                 app=apiomat-yambas,release=apiomat-yambas
Type:                     NodePort
IP:                       172.24.26.192
Port:                     http  8081/TCP
TargetPort:               8081/TCP
NodePort:                 http  31176/TCP
Endpoints:                172.16.1.11:8081,172.16.7.44:8081
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
