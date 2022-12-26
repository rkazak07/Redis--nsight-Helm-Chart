## Redis Insight Helm Chart Deploy

The Values.yaml File contains Deployment and Service. We revise it according to our own system. We give the information of our repo to Containers in Deployment.


## Quick Installation

```bash
$ helm  install my-release . -f values.yaml -n redis-insight --create-namespace
```


## Delete Chart

```bash
$ helm delete -n redis-insight my-release
```

## Configuration

The following table lists the configurable parameters of the mssql chart and their default values.

| Parameter                                      | Description                                                                                                                                           | Default                           |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| `image.repository`                     | `redis-insight` image repository                                                                                                                            | `mcr.microsoft.com/mssql/server`                |
| `image.tag`                            | `redis-insight` image tag                                                                                                                                   | `2019-latest`                         |
| `image.pullPolicy`                     | Image pull policy                                                                                                                                     | `IfNotPresent`                    |
| `replicaCount`                             | The number of mssql instances in the cluster. The chart will automatic create assign master to one of replicaCount                                      | `1`                               |
| `resources`                            | CPU/Memory resource requests/limits                                                                                                                   | Memory: `4096i`, CPU: `100m`     |
| `nodeSelector`                         | redis-insight server pod assignment                                                                                                                         | `{}`                              |
| `affinity`                             | redis-insight server affinity                                                                                                                               | `{}`                              |
| `tolerations`                          | redis-insight server tolerations                                                                                                                            | `[]`                              |
| `nodeSelector`                         | redis-insight server node selector                                                                                                                          | `{}`                              |
| `podSecurityContext`                   | Set security context for defining privilege and accessing control settings entire Pod                                                                 | `{}`                              |
| `securityContext`                      | Set security context for defining privilege and accessing control settings for couchbase container                                                      | `privileged: false`               |
| `service.type`                         | Kubernetes Service type                                                                                                                               | `ClusterIP`                       |
| `service.port`                         | redis-insight Service port                                                                                                                                  | `9000`                            |
| `podAnnotations`                       | Kubernetes Pod annotations                                                                                                                            | `{}`                              |
| `pvc.storageClass`             | Storage class of backing PVC (uses storage class annotation)                                                                                          | `nil`                             |
| `pvc.mssqlDataMode`               | Use volume as ReadOnly or ReadWrite                                                                                                                   | `ReadWriteOnce`                   |
| `pvc.DataSize`                     | Size of data volume                                                                                                                                   | `50Gi`                            |
| `ingress.enabled`                      | If true, mssql Ingress will be created                                                                                                          |
| `ingress.port`                         | redis-insight Ingress port                                                                                                                                  | `false`                           |
| `ingress.annotations`                  | redis-insight Ingress annotations                                                                                                                           | `{}`                              |
| `ingress.hosts`                        | redis-insight Ingress host names                                                                                                                            | `[]`                              |
| `ingress.paths`                        | redis-insight path parameters                                                                                                                           | `[]`                              |
| `ingress.tls`                          | redis-insight Ingress TLS configuration (YAML)                                                                                                              | `[]`                              |                                                                     
| `serviceAccount.create`                        | If true, create the redis-insight service account                                                                                                           | `true`                            |
| `autoscaling.enabled`                        | If true, autoscaling enabled                                                                                                          | `false`                            |
| `autoscaling.minreplicas`                        | minimum replica count                                                                                                     | `1`                            |
| `autoscaling.maxReplicas`                        | maximum replica count                                                                                                          | `100`                            |
| `autoscaling.targetCPUUtilizationPercentage`                        | Target cpu utilization  percentage                                                                                                      | `100`                            |
| `serviceAccount.name`                          | Name of the server service account to use or create                                                                                                   | `{{ fullname }}`          |
| `serviceAccount.annotations`                   | Service Account annotations                                                                                                                           | `{}`                              |
| `imagePullSecrets`                             | Configuration for imagePullSecrets so that you can use a private registry for your images                                                        | `[]`                              |



