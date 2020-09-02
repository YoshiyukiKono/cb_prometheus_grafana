# Install the Operator on Kubernetes

https://docs.couchbase.com/operator/current/install-kubernetes.html

## Prerequisites
Download `couchbase-autonomous-operator-kubernetes_2.0.1-macos-x86_64.zip` and unzip it.
You will find the following files.

```
$ cd couchbase-autonomous-operator-kubernetes_2.0.1-macos-x86_64 
$ ls -l
total 200
-rw-rw-r--@ 1 yoshiyuki.kono  staff  43198 May 22 03:06 License.txt
-rw-rw-r--@ 1 yoshiyuki.kono  staff   1996 May 22 03:06 README.txt
-rw-rw-r--@ 1 yoshiyuki.kono  staff     10 May 22 03:06 VERSION.txt
drwxrwxr-x@ 5 yoshiyuki.kono  staff    160 May 22 03:07 bin
-rw-rw-r--@ 1 yoshiyuki.kono  staff    591 May 22 03:06 couchbase-cluster.yaml
-rw-rw-r--@ 1 yoshiyuki.kono  staff  35202 May 22 03:06 crd.yaml
-rw-rw-r--@ 1 yoshiyuki.kono  staff    498 May 22 03:06 pillowfight-data-loader.yaml
-rw-rw-r--@ 1 yoshiyuki.kono  staff   1987 May 22 03:06 sync-gateway.yaml
$ ls -l bin
total 207304
-rwxrwxr-x@ 1 yoshiyuki.kono  staff  19833696 May 22 03:07 cbopcfg
-rwxrwxr-x@ 1 yoshiyuki.kono  staff  42253840 May 22 03:07 cbopconv
-rwxrwxr-x@ 1 yoshiyuki.kono  staff  44044960 May 22 03:07 cbopinfo
REML0693:couchbase-autonomous-operator-kubernetes_2.0.1-macos-x86_64 yoshiyuki.kono$ 
```

## Install CRD(Custom Resoure Definitions)

```
$ kubectl create -f crd.yaml
```

## Install the Operator

```
$ bin/cbopcfg | kubectl create -f -
```
## Check the status of the Operator
```
$ kubectl get deployments
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
couchbase-operator             1/1     1            1           25s
couchbase-operator-admission   1/1     1            1           26s
```

## Uninstall the Operator
I have not executed this yet.
```
$ bin/cbopcfg | kubectl delete -f -
$ kubectl delete -f crd.yaml
```
