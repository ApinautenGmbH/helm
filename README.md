# Versions

## Yambas

[3.2.0](https://apinautengmbh.github.io/helm/apiomat-yambas-3.2.0.tgz)
[3.2.1](https://helm.apiomat.com/apiomat-yambas-3.2.1-0.tgz)

## Dashboard

[3.2.4](https://helm.apiomat.com/apiomat-dashboard-3.2.4-0.tgz)

# Helm

Look at https://docs.helm.sh/using_helm/
and init with

```bash
helm init
```

## Package helm charts

```bash
helm package apiomat-yambas
helm package apiomat-dashboard
helm package apiomat-lurker
helm package apiomat-instructor
helm package apiomat-explorer
```

## Create repo index

```bash
helm repo index . --url https://<repo_full_url>
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

helm install --values apiomat-lurker/values.yaml apiomat-lurker/ --name "apiomat-lurker"

helm install --values apiomat-instructor/values.yaml apiomat-instructor/ --name "apiomat-instructor"

helm install --values apiomat-explorer/values.yaml apiomat-explorer/ --name "apiomat-explorer"
```
