# logstash-helm-chart
This is a Logstash helm chart that is part of the ELK stack.
# Getting Started
1. Create `monitoring` namespace, by running the following command:
```shell
kubectl create ns monitoring
```
2. Pull `logstash` dependencies, by running the following command:
```shell
helm dependency update ./logstash-helm-chart
```
3. Create a secret that will hold elasticsearch credentials. It should look like this:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: logstash-elastic-secret
  namespace: monitoring
data:
  username: ZWxhc3RpYw==
  password: RWxhc3RpYzJQYXNzd29yZA==
```
4. Install the chart, by running this command:
```shell
helm install logstash logstash-helm-chart -f logstash-helm-chart/values.yaml -n monitoring
```

Setting up for Netflow
```bash
bin/logstash --modules netflow --setup -M netflow.var.elasticsearch.hosts=elastic.database:9200 -M netflow.var.elasticsearch.username=Elastic2Passwordroot -M netflow.var.elasticsearch.password=Elastic2Passwordroot -M netflow.var.kibana.host=10.96.195.40:5601 -M netflow.var.kibana.username=elastic -M netflow.var.kibana.password=Elastic2Passwordroot -M netflow.var.kibana.scheme=http -M netflow.var.kibana.ssl.enabled=false -M netflow.var.kibana.ssl.verification_mode=disable -M netflow.var.input.udp.port=2055 --path.data /usr/share/logstash/netflow-data --path.logs /usr/share/logstash/logstash.log

```

