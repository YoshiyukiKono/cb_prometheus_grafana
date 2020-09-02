# Couchbase Cluster

https://docs.couchbase.com/operator/current/howto-couchbase-create.html

## Prepare the Couchbase Cluster Configuration

I just added the following part to the end of the original `couchbase-cluster.yaml` included in Autonomous Operator 2.0 zip file. (The file is [here](./yaml/couchbase-cluster-monitoring-aks.yaml))

Source: [Step-by-step Guide for Running Couchbase Autonomous Operator 2.0 with Prometheus (Part 1)](https://blog.couchbase.com/step-by-step-guide-for-running-couchbase-autonomous-operator-2-0-with-prometheus-part-1/)

Please note that AWS is used.

```
  monitoring:
    prometheus:
      enabled: true
      image: couchbase/exporter:1.0.1
      resources:
        requests:
          cpu: 100m
          memory: 100Mi
```

## Deploy the Couchbase Cluster

```
$ kubectl create -f couchbase-cluster.yaml
```

## Verify the Deployment
```
$ kubectl get pods
NAME                                           READY   STATUS    RESTARTS   AGE
cb-example-0000                                2/2     Running   0          19h
cb-example-0001                                2/2     Running   0          19h
cb-example-0002                                2/2     Running   0          19h
couchbase-operator-86588668b8-gn8bv            1/1     Running   0          23h
couchbase-operator-admission-5b487d7cb-thl7p   1/1     Running   0          23h
```
