# ociopensearchfluentbit


k create ns logging

k apply -f fluent-bit-service-account.yaml

k apply -f fluent-bit-role-1.22.yaml

k apply -f fluent-bit-role-binding-1.22.yaml

k apply -f fluent-bit-ds.yaml

curl -XGET 'https://10.0.0.110:9200/_cat/indices?v&pretty' --insecure

We using fluent bit to pump the cpu metrics and containers log into opensearch. It is based on DaemonSet. If seperate logs is require then  fluent-bit need to configre as a sidecar.

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opnesearch1.JPG)

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opnesearch2.JPG)