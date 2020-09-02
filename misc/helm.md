Note: Helmの最新版で、RBACが実装されたため、Tillerをセットアップする手順は不要になった。（出所要確認）

https://qiita.com/reoring/items/e50877f543bed72d93ee

```
brew install kubernetes-helm
```

```
vi clusterrole.yml
```

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  annotations:
    rbac.authorization.kubernetes.io/autoupdate: "true"
  labels:
    kubernetes.io/bootstrapping: rbac-defaults
  name: cluster-admin
rules:
- apiGroups:
  - '*'
  resources:
  - '*'
  verbs:
  - '*'
- nonResourceURLs:
  - '*'
  verbs:
  - '*'
```

```
minikube start
kubectl create -f clusterrole.yaml
```


```
kubectl create serviceaccount -n kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
```

https://www.jforte.me/2020/01/getting-started-with-helm-v3/
```
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
```


