# Sensu Go Deployment Chart

These helm chart deploy Sensu-Go with ETCD Cluster using etcd-operator chart in Kubernetes in the same namespace. 


## Usage

First update chart dependencies:
```sh
helm dependency update
```

Deploy it in a namespace:
```sh
helm upgrade --install sensu-backend --namespace sensu .
```

Scaling up:
```sh
kubectl scale deployment/sensu-backend --replicas=3
```

To deploy with ingress:
```sh
helm upgrade --install sensu-backend --namespace sensu --set-string ingress.enabled=true .
```

To test deployment:
```sh
helm test sensu-backend
```

## To use an external ETCD:

```sh
helm upgrade --install sensu-backend --namespace sensu --set-string etcdEndpoint="http://externaletcd.domain:2379" --set-string etcdDependency=false .
```


## References:

[sensu-go](https://docs.sensu.io/sensu-go/latest)    
[etcd-operator](https://github.com/helm/charts/tree/master/stable/etcd-operator)