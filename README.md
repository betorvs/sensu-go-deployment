# Sensu Go Deployment Chart

Travis CI: [![Build Status](https://travis-ci.org/betorvs/sensu-go-deployment.svg?branch=master)](https://travis-ci.org/betorvs/sensu-go-deployment)

These helm chart deploy Sensu-Go with ETCD Cluster using etcd-operator chart in Kubernetes in the same namespace. 


## Deploy

You can use this direcly as a helm repository or download these and install manually.

### Usage 


Install the helm repository and install sensu chart:

```sh
helm repo add betorvs https://betorvs.github.io/sensu-go-deployment/
helm repo update
helm upgrade --install sensu-backend --namespace sensu betorvs/sensu-go-deployment
```

### Manually using these repository

First update chart dependencies:
```sh
helm dependency update
```

Deploy it in a namespace:
```sh
helm upgrade --install sensu-backend --namespace sensu .
```

### To Scale 

Scaling up:
```sh
kubectl scale deployment/sensu-backend --replicas=3
```

### With ingress

To deploy with ingress:
```sh
helm upgrade --install sensu-backend --namespace sensu --set-string ingress.enabled=true .
```

### To test the deployment

To test deployment:
```sh
helm test sensu-backend
```


### To use an external ETCD:

```sh
helm upgrade --install sensu-backend --namespace sensu --set-string etcdEndpoint="http://externaletcd.domain:2379" --set-string etcdDependency=false .
```


## References:

[sensu-go](https://docs.sensu.io/sensu-go/latest)    
[etcd-operator](https://github.com/helm/charts/tree/master/stable/etcd-operator)