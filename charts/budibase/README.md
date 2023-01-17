# budibase

_Based on [openvpn-as](https://github.com/Budibase/budibase/tree/develop/charts/budibase) chart from [Budibase](https://github.com/Budibase)._

## TL;DR

```sh
helm repo add londonbridge https://london-bridge.github.io/helm-charts
helm install my-release --set 'service.type=LoadBalancer' londonbridge/budibase
```

## Introduction

This chart installs `budibase` on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.0+
- LoadBalancer to expose the service
- PV provisioner support in the underlying infrastructure (with persistence storage enabled)

## Installing the Chart

To install the chart with the release name `my-release`:

```sh
helm repo add londonbridge https://london-bridge.github.io/helm-charts
helm install my-release --set 'service.type=LoadBalancer' londonbridge/budibase
```

These commands deploy budibase on the Kubernetes cluster in the default configuration. The [Parameters](./#parameters) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```sh
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables list the configurable parameters of the budibase chart and their default values.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| couchdb.affinity | object | `{}` |  |
| couchdb.allowAdminParty | bool | `false` |  |
| couchdb.annotations | object | `{}` |  |
| couchdb.clusterSize | int | `3` |  |
| couchdb.couchdbConfig.chttpd.bind_address | string | `"any"` |  |
| couchdb.couchdbConfig.chttpd.require_valid_user | bool | `false` |  |
| couchdb.couchdbConfig.couchdb.uuid | string | `"budibase-couchdb"` |  |
| couchdb.createAdminSecret | bool | `true` |  |
| couchdb.dns.clusterDomainSuffix | string | `"cluster.local"` |  |
| couchdb.enableSearch | bool | `true` |  |
| couchdb.erlangFlags.name | string | `"couchdb"` |  |
| couchdb.erlangFlags.setcookie | string | `"monster"` |  |
| couchdb.image.pullPolicy | string | `"IfNotPresent"` |  |
| couchdb.image.repository | string | `"couchdb"` |  |
| couchdb.image.tag | string | `"3.2.1"` |  |
| couchdb.ingress.annotations | list | `[]` |  |
| couchdb.ingress.enabled | bool | `false` |  |
| couchdb.ingress.hosts[0] | string | `"chart-example.local"` |  |
| couchdb.ingress.path | string | `"/"` |  |
| couchdb.ingress.tls | string | `nil` |  |
| couchdb.initImage.pullPolicy | string | `"Always"` |  |
| couchdb.initImage.repository | string | `"busybox"` |  |
| couchdb.initImage.tag | string | `"latest"` |  |
| couchdb.livenessProbe.enabled | bool | `true` |  |
| couchdb.livenessProbe.failureThreshold | int | `3` |  |
| couchdb.livenessProbe.initialDelaySeconds | int | `0` |  |
| couchdb.livenessProbe.periodSeconds | int | `10` |  |
| couchdb.livenessProbe.successThreshold | int | `1` |  |
| couchdb.livenessProbe.timeoutSeconds | int | `1` |  |
| couchdb.networkPolicy.enabled | bool | `true` |  |
| couchdb.persistentVolume.accessModes[0] | string | `"ReadWriteOnce"` |  |
| couchdb.persistentVolume.enabled | bool | `false` |  |
| couchdb.persistentVolume.size | string | `"10Gi"` |  |
| couchdb.persistentVolume.storageClass | string | `""` |  |
| couchdb.podManagementPolicy | string | `"Parallel"` |  |
| couchdb.readinessProbe.enabled | bool | `true` |  |
| couchdb.readinessProbe.failureThreshold | int | `3` |  |
| couchdb.readinessProbe.initialDelaySeconds | int | `0` |  |
| couchdb.readinessProbe.periodSeconds | int | `10` |  |
| couchdb.readinessProbe.successThreshold | int | `1` |  |
| couchdb.readinessProbe.timeoutSeconds | int | `1` |  |
| couchdb.resources | object | `{}` |  |
| couchdb.searchImage.pullPolicy | string | `"IfNotPresent"` |  |
| couchdb.searchImage.repository | string | `"kocolosk/couchdb-search"` |  |
| couchdb.searchImage.tag | string | `"0.2.0"` |  |
| couchdb.service.enabled | bool | `true` |  |
| couchdb.service.externalPort | int | `5984` |  |
| couchdb.service.type | string | `"ClusterIP"` |  |
| couchdb.serviceAccount.create | bool | `true` |  |
| couchdb.serviceAccount.enabled | bool | `true` |  |
| couchdb.tolerations | list | `[]` |  |
| globals.accountPortalApiKey | string | `""` |  |
| globals.accountPortalUrl | string | `""` |  |
| globals.appVersion | string | `"latest"` |  |
| globals.automationMaxIterations | string | `"200"` |  |
| globals.budibaseEnv | string | `"PRODUCTION"` |  |
| globals.cdnUrl | string | `""` |  |
| globals.cookieDomain | string | `""` |  |
| globals.createSecrets | bool | `true` |  |
| globals.enableAnalytics | string | `"1"` |  |
| globals.google.clientId | string | `""` |  |
| globals.google.secret | string | `""` |  |
| globals.httpMigrations | string | `"0"` |  |
| globals.internalApiKey | string | `""` |  |
| globals.jwtSecret | string | `""` |  |
| globals.logLevel | string | `"info"` |  |
| globals.multiTenancy | string | `"0"` |  |
| globals.platformUrl | string | `""` |  |
| globals.posthogToken | string | `""` |  |
| globals.selfHosted | string | `"1"` |  |
| globals.sentryDSN | string | `""` |  |
| globals.smtp.enabled | bool | `false` |  |
| globals.tenantFeatureFlags | string | `"*:LICENSING,*:USER_GROUPS"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"nginx"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/client-max-body-size" | string | `"150M"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-body-size" | string | `"50m"` |  |
| ingress.aws | bool | `false` |  |
| ingress.certificateArn | string | `""` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `nil` |  |
| ingress.hosts[0].paths[0].backend.service.name | string | `"proxy-service"` |  |
| ingress.hosts[0].paths[0].backend.service.port.number | int | `10000` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.nginx | bool | `true` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `10000` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| services.apps.logLevel | string | `"info"` |  |
| services.apps.port | int | `4002` |  |
| services.apps.replicaCount | int | `1` |  |
| services.apps.resources | object | `{}` |  |
| services.budibaseVersion | string | `"latest"` |  |
| services.couchdb.backup.enabled | bool | `false` |  |
| services.couchdb.backup.interval | string | `""` |  |
| services.couchdb.backup.resources | object | `{}` |  |
| services.couchdb.backup.target | string | `""` |  |
| services.couchdb.enabled | bool | `true` |  |
| services.couchdb.port | int | `5984` |  |
| services.dns | string | `"cluster.local"` |  |
| services.objectStore.accessKey | string | `""` |  |
| services.objectStore.browser | bool | `true` |  |
| services.objectStore.cloudfront.cdn | string | `""` |  |
| services.objectStore.cloudfront.privateKey64 | string | `""` |  |
| services.objectStore.cloudfront.publicKeyId | string | `""` |  |
| services.objectStore.minio | bool | `true` |  |
| services.objectStore.port | int | `9000` |  |
| services.objectStore.region | string | `""` |  |
| services.objectStore.replicaCount | int | `1` |  |
| services.objectStore.resources | object | `{}` |  |
| services.objectStore.secretKey | string | `""` |  |
| services.objectStore.storage | string | `"100Mi"` |  |
| services.objectStore.storageClass | string | `""` |  |
| services.objectStore.url | string | `"http://minio-service:9000"` |  |
| services.proxy.port | int | `10000` |  |
| services.proxy.replicaCount | int | `1` |  |
| services.proxy.resources | object | `{}` |  |
| services.proxy.upstreams.apps | string | `"http://app-service.{{ .Release.Namespace }}.svc.{{ .Values.services.dns }}:{{ .Values.services.apps.port }}"` |  |
| services.proxy.upstreams.couchdb | string | `"http://{{ .Release.Name }}-svc-couchdb:{{ .Values.services.couchdb.port }}"` |  |
| services.proxy.upstreams.minio | string | `"http://minio-service.{{ .Release.Namespace }}.svc.{{ .Values.services.dns }}:{{ .Values.services.objectStore.port }}"` |  |
| services.proxy.upstreams.worker | string | `"http://worker-service.{{ .Release.Namespace }}.svc.{{ .Values.services.dns }}:{{ .Values.services.worker.port }}"` |  |
| services.redis.enabled | bool | `true` |  |
| services.redis.password | string | `"budibase"` |  |
| services.redis.port | int | `6379` |  |
| services.redis.replicaCount | int | `1` |  |
| services.redis.resources | object | `{}` |  |
| services.redis.storage | string | `"100Mi"` |  |
| services.redis.storageClass | string | `""` |  |
| services.redis.url | string | `""` |  |
| services.worker.port | int | `4003` |  |
| services.worker.replicaCount | int | `1` |  |
| services.worker.resources | object | `{}` |  |
| tolerations | list | `[]` |  |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```sh
helm install my-release -f ./values.yaml londonbridge/budibase
```
