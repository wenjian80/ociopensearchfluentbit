# ociopensearchfluentbit


k create ns logging
k apply -f fluent-bit-service-account.yaml
k apply -f fluent-bit-role-1.22.yaml
k apply -f fluent-bit-role-binding-1.22.yaml
k apply -f fluent-bit-ds.yaml

curl -XGET 'https://10.0.0.110:9200/_cat/indices?v&pretty' --insecure