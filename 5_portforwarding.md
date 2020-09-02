# Portforwarding

https://blog.couchbase.com/step-by-step-guide-for-running-couchbase-autonomous-operator-2-0-with-prometheus-part-2/

```
$ kubectl --namespace default port-forward svc/cb-example 8091 &
$ kubectl --namespace monitoring port-forward svc/prometheus-k8s 9090 &
$ kubectl --namespace monitoring port-forward svc/grafana 3000 &
$ kubectl --namespace monitoring port-forward svc/alertmanager-main 9093 &
$ kubectl --namespace monitoring port-forward svc/node-exporter 9100 &
$ kubectl --namespace default port-forward svc/couchbase-metrics 9091 &

Forwarding from [::1]:9093 -> 9093
Forwarding from [::1]:8091 -> 8091
Forwarding from 127.0.0.1:3000 -> 3000
Forwarding from [::1]:3000 -> 3000
Forwarding from 127.0.0.1:9100 -> 9100
Forwarding from [::1]:9100 -> 9100
Forwarding from 127.0.0.1:9090 -> 9090
Forwarding from [::1]:9090 -> 9090
Forwarding from 127.0.0.1:9091 -> 9091
Forwarding from [::1]:9091 -> 9091
```
