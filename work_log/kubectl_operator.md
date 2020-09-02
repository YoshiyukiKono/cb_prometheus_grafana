
https://docs.couchbase.com/operator/current/howto-ui.html
https://docs.couchbase.com/operator/current/howto-ui.html

```
REML0693:AKS yoshiyuki.kono$ kubectl create -f crd.yaml
customresourcedefinition.apiextensions.k8s.io/couchbasebuckets.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbaseephemeralbuckets.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbasememcachedbuckets.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbasereplications.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbaseusers.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbasegroups.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbaserolebindings.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbaseclusters.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbasebackups.couchbase.com created
customresourcedefinition.apiextensions.k8s.io/couchbasebackuprestores.couchbase.com created
REML0693:AKS yoshiyuki.kono$ /Users/yoshiyuki.kono/Documents/autonomous_operator/couchbase-autonomous-operator-kubernetes_2.0.1-macos-x86_64/bin/cbopcfg | kubectl create -f -
serviceaccount/couchbase-operator-admission created
clusterrole.rbac.authorization.k8s.io/couchbase-operator-admission created
clusterrolebinding.rbac.authorization.k8s.io/couchbase-operator-admission created
secret/couchbase-operator-admission created
deployment.apps/couchbase-operator-admission created
service/couchbase-operator-admission created
mutatingwebhookconfiguration.admissionregistration.k8s.io/couchbase-operator-admission created
validatingwebhookconfiguration.admissionregistration.k8s.io/couchbase-operator-admission created
serviceaccount/couchbase-operator created
role.rbac.authorization.k8s.io/couchbase-operator created
rolebinding.rbac.authorization.k8s.io/couchbase-operator created
deployment.apps/couchbase-operator created
service/couchbase-operator created
REML0693:AKS yoshiyuki.kono$ kubectl get deployments
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
couchbase-operator             1/1     1            1           25s
couchbase-operator-admission   1/1     1            1           26s
REML0693:AKS yoshiyuki.kono$ vi couchbase-cluster.yaml
REML0693:AKS yoshiyuki.kono$ kubectl create -f couchbase-cluster.yaml
secret/cb-example-auth created
couchbasebucket.couchbase.com/default created
couchbasecluster.couchbase.com/cb-example created
REML0693:AKS yoshiyuki.kono$ kubectl get deployments
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
couchbase-operator             1/1     1            1           2m6s
couchbase-operator-admission   1/1     1            1           2m7s
REML0693:AKS yoshiyuki.kono$ kubectl get pods
NAME                                           READY   STATUS              RESTARTS   AGE
cb-example-0000                                0/1     ContainerCreating   0          3s
couchbase-operator-86588668b8-gn8bv            1/1     Running             0          2m18s
couchbase-operator-admission-5b487d7cb-thl7p   1/1     Running             0          2m19s
REML0693:AKS yoshiyuki.kono$ kubectl get pods
NAME                                           READY   STATUS              RESTARTS   AGE
cb-example-0000                                0/1     ContainerCreating   0          26s
couchbase-operator-86588668b8-gn8bv            1/1     Running             0          2m41s
couchbase-operator-admission-5b487d7cb-thl7p   1/1     Running             0          2m42s
REML0693:AKS yoshiyuki.kono$ kubectl get pods
NAME                                           READY   STATUS    RESTARTS   AGE
cb-example-0000                                1/1     Running   0          2m23s
cb-example-0001                                1/1     Running   0          98s
cb-example-0002                                1/1     Running   0          53s
couchbase-operator-86588668b8-gn8bv            1/1     Running   0          4m38s
couchbase-operator-admission-5b487d7cb-thl7p   1/1     Running   0          4m39s
REML0693:AKS yoshiyuki.kono$ kubectl port-forward cb-example-0000 8091
Forwarding from 127.0.0.1:8091 -> 8091
Forwarding from [::1]:8091 -> 8091
Handling connection for 8091
Handling connection for 8091

```
