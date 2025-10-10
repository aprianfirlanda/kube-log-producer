# README

verify the fluentbit working

```shell
kubectl -n logging get pods -l app=fluent-bit
kubectl -n logging logs -l app=fluent-bit --tail=200
```

check data on opensearch
```shell
curl -sku admin:Pratista17 "https://192.168.100.114:9200/_cat/indices?v" | grep sikd
```

how to change from minio to netapp
```shell
kubectl -n logging create secret generic fluent-bit-outputs \
  --from-literal=S3_ENDPOINT='netapp-s3.example.com:443' \
  --from-literal=S3_ACCESS_KEY='...' \
  --from-literal=S3_SECRET_KEY='...' \
  --dry-run=client -o yaml | kubectl apply -f -
```
