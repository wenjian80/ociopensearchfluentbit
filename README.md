# ociopensearchfluentbit


k create ns logging

k apply -f fluent-bit-service-account.yaml

k apply -f fluent-bit-role-1.22.yaml

k apply -f fluent-bit-role-binding-1.22.yaml

DaemonSet example

k apply -f fluent-bit-ds.yaml

Side car example

k apply -f fluent-bit-sc.yaml

curl -XGET 'https://10.0.0.110:9200/_cat/indices?v&pretty' --insecure

We using fluent bit to pump the cpu metrics and containers log into opensearch. It is based on DaemonSet. If seperate logs is require then  fluent-bit need to configre as a sidecar.

Refer to https://github.com/wenjian80/ociopensearchfluentbit/blob/main/fluent-bit-sc.yaml for example of a side car instead of DaemonSet

if it pure vm refer to fluent bit installation on linux https://docs.fluentbit.io/manual/installation/linux

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opnesearch1.JPG)

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opensearch2.JPG)

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opensearchui.JPG)

