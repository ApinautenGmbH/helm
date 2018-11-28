## Install helm

Look at https://docs.helm.sh/using_helm/
and init with

# Versions

## Yambas

[3.1.2](https://apinautengmbh.github.io/helm/apiomat-yambas-0.2.1.tgz)

## Dashboard

[3.2.2](https://apinautengmbh.github.io/helm/apiomat-dashboard-0.2.1.tgz)

```bash
helm init
```

## Package helm charts

```bash
helm package apiomat-yambas
helm package apiomat-dashboard
```

## Create repo index

```bash
helm repo index .
```

## Install prerequisites helm charts
```bash
helm install --values mongodb-values.yaml stable/mongodb-replicaset --name "apiomat-mongodb"
helm install --values consul-values.yaml stable/consul --name "apiomat-consul" --namespace apiomat
```

## Install apiomat helm charts
```bash
helm install --values yambas-values.yaml  apiomat-yambas/ --name "apiomat-yambas" --namespace apiomat
# exec into one yambas container and run following command
curl -X POST http://localhost:8081/yambas/rest/initSuperAdmin -d "email=apinaut@apiomat.com&password=supers3cr3tpassword"


helm install --values apiomat-dashboard/values.yaml apiomat-dashboard/ --name "apiomat-dashboard"
```