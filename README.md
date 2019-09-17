# dbaas-px
Bunch of DB's for DBaaS on Kubernetes backed by Portworx

## Install Portworx
```
https://docs.portworx.com/portworx-install-with-kubernetes/
```
## Before you Begin
### Install helm
```
https://github.com/helm/helm/blob/master/docs/install.md
```

### Initialize helm
```
helm  init
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'
```

### Create the required storageClasses
```
kubectl apply -f manifests/portworx-storageclasses.yaml
```

## Install Mariadb
```
helm install --name mariadb --namespace mariadb --values manifests/mariadb-values.yaml helm-charts/mariadb
```