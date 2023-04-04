# helm-myapp

![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)  ![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square)

Instalacao de chart myapp

# Prerequisites

* Install the kubectl, helm and helm-docs commands following the instructions of the file [REQUIREMENTS.md](../REQUIREMENTS.md).

# Installing the Chart

* Access a Kubernetes cluster.

* Change the values according to the need of the environment in ``helm-myapp/values.yaml`` file. The [Parameters](#parameters) section lists the parameters that can be configured during installation.

* Test the installation with command:

```bash
helm upgrade --install helm-myapp -f helm-myapp/values.yaml helm-myapp/ -n helm-myapp --create-namespace --dry-run
```

* To install/upgrade the chart with the release name `helm-myapp`:

```bash
helm upgrade --install helm-myapp -f helm-myapp/values.yaml helm-myapp/ -n helm-myapp --create-namespace
```

Create a port-forward with the follow command:

```bash
kubectl port-forward svc/helm-myapp 3000:80 -n helm-myapp
```

Open the browser and access the URL: http://localhost:3000

## Uninstalling the Chart

To uninstall/delete the `helm-myapp` deployment:

```bash
helm uninstall helm-myapp -n helm-myapp
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

The following tables lists the configurable parameters of the chart and their default values.

Change the values according to the need of the environment in ``helm-myapp/values.yaml`` file.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `20` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"aeciopires/kube-pires"` |  |
| image.tag | string | `"1.0.0"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| livenessProbe | object | `{"failureThreshold":3,"initialDelaySeconds":5,"path":"/health","periodSeconds":10,"successThreshold":1,"timeoutSeconds":5}` | Healh check continuos |
| livenessProbe.failureThreshold | int | `3` | When a probe fails, Kubernetes will try failureThreshold times before giving up. Giving up in case of liveness probe means restarting the container. In case of readiness probe the Pod will be marked Unready |
| livenessProbe.initialDelaySeconds | int | `5` | Number of seconds after the container has started before liveness |
| livenessProbe.path | string | `"/health"` | Path of health check of application |
| livenessProbe.periodSeconds | int | `10` | Specifies that the kubelet should perform a liveness probe every N seconds |
| livenessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed |
| livenessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out |
| mySecret | object | `{"enabled":true,"mySecretDistributedTracingEnabled":"true","mySecretHighSecurity":"false","mySecretLicenseKey":"mysecurepassword2"}` | Configurations of the application. Create configMap and Secret for use in deployment as environment variable |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | Node selector configurations |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe | object | `{"failureThreshold":3,"initialDelaySeconds":5,"path":"/health","periodSeconds":10,"successThreshold":1,"timeoutSeconds":5}` | Health check on creation pod |
| readinessProbe.failureThreshold | int | `3` | When a probe fails, Kubernetes will try failureThreshold times before giving up. Giving up in case of liveness probe means restarting the container. In case of readiness probe the Pod will be marked Unready |
| readinessProbe.initialDelaySeconds | int | `5` | Number of seconds after the container has started before readiness |
| readinessProbe.path | string | `"/health"` | Path of health check of application |
| readinessProbe.periodSeconds | int | `10` | Specifies that the kubelet should perform a liveness probe every N seconds |
| readinessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed |
| readinessProbe.timeoutSeconds | int | `5` | Number of seconds after which the probe times out |
| replicaCount | int | `2` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"5m"` |  |
| resources.requests.memory | string | `"5Mi"` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` | Tolerations configurations |
