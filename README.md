# vault-cluster
Deploying Vault &amp; Consul into Kubernetes

## Consul cluster

In order to deploy the consul cluster, firstly the `consul-service.yml` must be applied:

```
kubectl create -f consul-service.yml
```

The configuration must be imported. This includes a CA chain and a series of certificates and
server keys which are not included in this repository.

```
kubectl create configmap --from-file=ca.pem=consul-ca.cer.pem consul-ca-config 
```

### Joining the cluster 

In order to join the cluster members together, create the `consul-joiner` job:

```
kubectl create -f consul-joiner.yml
```