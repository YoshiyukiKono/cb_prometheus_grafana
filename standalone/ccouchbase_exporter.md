Note: Couchbase Exporterを利用したPrometeus連携は、サーバーへのインストールでは、成功した。一方、Autonomous Operatorを使った場合、YAMLファイルにmonitoringセクションを加えることで連携ができることが確認できた。（関連性要確認）

https://github.com/totvslabs/couchbase-exporter/releases
```
curl -OL https://github.com/totvslabs/couchbase-exporter/releases/download/v1.6.0/couchbase-exporter_1.6.0_linux_amd64.tar.gz
tar xvzf couchbase-exporter_1.6.0_linux_amd64.tar.gz 
```

```
$ ls -l
total 12696
-rwxr-xr-x. 1 ec2-user ec2-user 9338880 Apr 28 18:52 couchbase-exporter
-rw-rw-r--. 1 ec2-user ec2-user 3646035 Aug 28 01:32 couchbase-exporter_1.6.0_linux_amd64.tar.gz
-rw-r--r--. 1 root     root       11896 Aug 28 00:50 couchbase-release-1.0-x86_64.rpm
drwxrwxr-x. 2 ec2-user ec2-user      28 Aug 28 01:32 grafana
drwxrwxr-x. 3 ec2-user ec2-user      41 Aug 28 01:32 prometheus
```

password: couchbase (not password)
```
./couchbase-exporter --couchbase.username Administrator --couchbase.password couchbase --web.listen-address=":9420" --couchbase.url="http://localhost:8091"
couchbase.url="http://localhost:8091"
INFO[0000] starting couchbase-exporter 1.6.0...          source="main.go:38"
INFO[0000] server listening on :9420                     source="main.go:69"
WARN[0000] couchbase 6.6.0-7909-enterprise is not fully supported  source="couchbase.go:38"
```

```
./couchbase-exporter --couchbase.username Administrator --couchbase.password couchbase --web.listen-address=":9421" --couchbase.url="http://localhost:8091"
couchbase.url="http://localhost:8091"
INFO[0000] starting couchbase-exporter 1.6.0...          source="main.go:38"
INFO[0000] server listening on :9420                     source="main.go:69"
WARN[0000] couchbase 6.6.0-7909-enterprise is not fully supported  source="couchbase.go:38"
```
