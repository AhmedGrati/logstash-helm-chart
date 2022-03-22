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
