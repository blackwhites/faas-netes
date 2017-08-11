QuickStart
==========

### Deploy OpenFaaS on Kubernetes

OpenFaaS is a framework for building serverless applications with the power of containers. Just bring your favorite orchestration platform - Docker Swarm or Kubernetes.

* Clone the code

```
$ git clone https://github.com/alexellis/faas-netes
```

* Deploy the services

```
$ cd faas-netes
$ kubectl apply -f ./faas.yml,monitoring.yml,rbac.yml
```

That's it. You now have OpenFaaS deployed.

For simplicity the default configuration uses NodePorts rather than an IngressController (which is more complicated to setup).

| Service           | TCP port |
--------------------|----------|
| API Gateway / UI  | 31112    |
| Prometheus        | 31119    |

> If you're an advanced Kubernetes user, you can add an IngressController to your stack and remove the NodePort assignments.

* Deploy a sample function

There are currently no sample functions built into this stack, but we can deploy them quickly via the UI or FaaS-CLI.

Click "New Function" and fill it out with the following:

| Field      | Value                        |
-------------|------------------------------|
| Service    | nodeinfo                     |
| Image      | functions/nodeinfo:latest    |
| fProcess   | node main.js                 |
| Network    | default                      |

* Test the function

Your function will appear after a few seconds and you can click "Invoke"

For more - head over to the [main FaaS repo](https://github.com/alexellis/faas).