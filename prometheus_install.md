```
curl -OL https://github.com/prometheus/prometheus/releases/download/v2.20.1/prometheus-2.20.1.linux-amd64.tar.gz
tar xvzf prometheus-2.20.1.linux-amd64.tar.gz 
cd prometheus-2.20.1.linux-amd64
./prometheus --config.file=prometheus.yml
```


```
scrape_configs:
 # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
 - job_name: 'couchbase'
 
   # metrics_path defaults to '/metrics'
   # scheme defaults to 'http'.
   static_configs:
 
   - targets: ['localhost:9420', 'localhost:9421']                                                
```
