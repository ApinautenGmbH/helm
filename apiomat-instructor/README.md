# Apiomat Instructor Helm Chart

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
Name:                     apiomat-instructor
Namespace:                apiomat
Labels:                   app=apiomat-instructor
                          chart=apiomat-instructor-x.x.x
                          heritage=Tiller
                          release=apiomat-instructor
Selector:                 app=apiomat-instructor,release=apiomat-instructor
Type:                     NodePort
IP:                       172.24.26.192
Port:                     http  8093/TCP
TargetPort:               8093/TCP
NodePort:                 http  31176/TCP
Endpoints:                172.16.1.11:8093,172.16.7.44:8093
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
