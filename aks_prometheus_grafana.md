https://blog.couchbase.com/step-by-step-guide-for-running-couchbase-autonomous-operator-2-0-with-prometheus-part-2/

```
git clone https://github.com/prometheus-operator/kube-prometheus.git
```

```
cd kube-prometheus/manifests
couchbase-serviceMonitor.yaml
```

```
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: couchbase
  namespace: default # <1>
  labels:
    app: couchbase
spec:
  endpoints:
  - port: metrics       # <2>
    interval: 5s        # <3>
  namespaceSelector:
    matchNames:
    - default # <4>
  selector:
    matchLabels:
      app: couchbase # <5>
```
```
vi couchbase-service.yaml
```

```
apiVersion: v1
kind: Service
metadata:
  name: couchbase-metrics
  namespace: default # <1>
  labels:
    app: couchbase
spec:
  ports:
  - name: metrics
    port: 9091 # <2>
    protocol: TCP
  selector:
    app: couchbase
    couchbase_cluster: cb-example # <3>
```

```
kubectl create namespace monitoring
```


```
$ kubectl create -f manifests/
secret/alertmanager-main created
service/alertmanager-main created
serviceaccount/alertmanager-main created
secret/grafana-datasources created
configmap/grafana-dashboard-apiserver created
configmap/grafana-dashboard-cluster-total created
configmap/grafana-dashboard-controller-manager created
configmap/grafana-dashboard-k8s-resources-cluster created
configmap/grafana-dashboard-k8s-resources-namespace created
configmap/grafana-dashboard-k8s-resources-node created
configmap/grafana-dashboard-k8s-resources-pod created
configmap/grafana-dashboard-k8s-resources-workload created
configmap/grafana-dashboard-k8s-resources-workloads-namespace created
configmap/grafana-dashboard-kubelet created
configmap/grafana-dashboard-namespace-by-pod created
configmap/grafana-dashboard-namespace-by-workload created
configmap/grafana-dashboard-node-cluster-rsrc-use created
configmap/grafana-dashboard-node-rsrc-use created
configmap/grafana-dashboard-nodes created
configmap/grafana-dashboard-persistentvolumesusage created
configmap/grafana-dashboard-pod-total created
configmap/grafana-dashboard-prometheus-remote-write created
configmap/grafana-dashboard-prometheus created
configmap/grafana-dashboard-proxy created
configmap/grafana-dashboard-scheduler created
configmap/grafana-dashboard-statefulset created
configmap/grafana-dashboard-workload-total created
configmap/grafana-dashboards created
deployment.apps/grafana created
service/grafana created
serviceaccount/grafana created
deployment.apps/kube-state-metrics created
service/kube-state-metrics created
serviceaccount/kube-state-metrics created
daemonset.apps/node-exporter created
service/node-exporter created
serviceaccount/node-exporter created
configmap/adapter-config created
deployment.apps/prometheus-adapter created
service/prometheus-adapter created
serviceaccount/prometheus-adapter created
rolebinding.rbac.authorization.k8s.io/prometheus-k8s-config created
rolebinding.rbac.authorization.k8s.io/prometheus-k8s created
role.rbac.authorization.k8s.io/prometheus-k8s-config created
role.rbac.authorization.k8s.io/prometheus-k8s created
service/prometheus-k8s created
serviceaccount/prometheus-k8s created
Error from server (AlreadyExists): error when creating "manifests/couchbase-service.yaml": services "couchbase-metrics" already exists
Error from server (AlreadyExists): error when creating "manifests/kube-state-metrics-clusterRole.yaml": clusterroles.rbac.authorization.k8s.io "kube-state-metrics" already exists
Error from server (AlreadyExists): error when creating "manifests/kube-state-metrics-clusterRoleBinding.yaml": clusterrolebindings.rbac.authorization.k8s.io "kube-state-metrics" already exists
Error from server (AlreadyExists): error when creating "manifests/node-exporter-clusterRole.yaml": clusterroles.rbac.authorization.k8s.io "node-exporter" already exists
Error from server (AlreadyExists): error when creating "manifests/node-exporter-clusterRoleBinding.yaml": clusterrolebindings.rbac.authorization.k8s.io "node-exporter" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-apiService.yaml": apiservices.apiregistration.k8s.io "v1beta1.metrics.k8s.io" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-clusterRole.yaml": clusterroles.rbac.authorization.k8s.io "prometheus-adapter" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-clusterRoleAggregatedMetricsReader.yaml": clusterroles.rbac.authorization.k8s.io "system:aggregated-metrics-reader" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-clusterRoleBinding.yaml": clusterrolebindings.rbac.authorization.k8s.io "prometheus-adapter" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-clusterRoleBindingDelegator.yaml": clusterrolebindings.rbac.authorization.k8s.io "resource-metrics:system:auth-delegator" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-clusterRoleServerResources.yaml": clusterroles.rbac.authorization.k8s.io "resource-metrics-server-resources" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-adapter-roleBindingAuthReader.yaml": rolebindings.rbac.authorization.k8s.io "resource-metrics-auth-reader" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-clusterRole.yaml": clusterroles.rbac.authorization.k8s.io "prometheus-k8s" already exists
Error from server (AlreadyExists): error when creating "manifests/prometheus-clusterRoleBinding.yaml": clusterrolebindings.rbac.authorization.k8s.io "prometheus-k8s" already exists
Error from server (AlreadyExists): rolebindings.rbac.authorization.k8s.io "prometheus-k8s" already exists
Error from server (AlreadyExists): rolebindings.rbac.authorization.k8s.io "prometheus-k8s" already exists
Error from server (AlreadyExists): roles.rbac.authorization.k8s.io "prometheus-k8s" already exists
Error from server (AlreadyExists): roles.rbac.authorization.k8s.io "prometheus-k8s" already exists
[unable to recognize "manifests/alertmanager-alertmanager.yaml": no matches for kind "Alertmanager" in version "monitoring.coreos.com/v1", unable to recognize "manifests/alertmanager-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/couchbase-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/grafana-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/kube-state-metrics-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/node-exporter-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-adapter-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-operator-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-prometheus.yaml": no matches for kind "Prometheus" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-rules.yaml": no matches for kind "PrometheusRule" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitor.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitorApiserver.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitorCoreDNS.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitorKubeControllerManager.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitorKubeScheduler.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1", unable to recognize "manifests/prometheus-serviceMonitorKubelet.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1"]
REML0693:kube-prometheus yoshiyuki.kono$ 
```
