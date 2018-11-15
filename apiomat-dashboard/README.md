# Apiomat Dashboard Helm Chart

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
Name:                     apiomat-dashboard
Namespace:                apiomat
Labels:                   app=apiomat-dashboard
                          chart=apiomat-dashboard-0.2.1
                          heritage=Tiller
                          release=apiomat-dashboard
Annotations:              traefik.backend.loadbalancer.method: drr
                          traefik.backend.loadbalancer.stickiness: true
                          traefik.frontend.passHostHeader: true
Selector:                 app=apiomat-dashboard,release=apiomat-dashboard
Type:                     NodePort
IP:                       172.24.26.192
Port:                     http  8000/TCP
TargetPort:               8000/TCP
NodePort:                 http  31176/TCP
Endpoints:                172.16.1.11:8000,172.16.7.44:8000
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```
