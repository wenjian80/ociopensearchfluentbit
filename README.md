# ociopensearchfluentbit

# Disclaimer
**Disclaimer: The information presented in this article is for educational/general information purposes only. Any scripts or examples are presented where-is, as-is, and are unsupported by Oracle Support and Development. Always refer to the official oracle documentation and other necessary documentation for offical steps.**

An oke and opensearch is provision within the same vcn


The parameter FLUENT_ELASTICSEARCH_HOST and FLUENT_ELASTICSEARCH_PORT has to be change to match your opensearch instance

# DaemonSet example
k create ns logging

k apply -f fluent-bit-service-account.yaml

k apply -f fluent-bit-role-1.22.yaml

k apply -f fluent-bit-role-binding-1.22.yaml

k apply -f fluent-bit-configmap.yaml

k apply -f fluent-bit-ds.yaml

# Side car example

k create ns logging

k apply -f fluent-bit-service-account.yaml

k apply -f fluent-bit-role-1.22.yaml

k apply -f fluent-bit-role-binding-1.22.yaml

k apply -f fluent-bit-sc.yaml

# Misc
curl -XGET 'https://10.0.0.110:9200/_cat/indices?v&pretty' --insecure

By default the index name will be starting with logstash-* for logs. Change prefix if we want to https://docs.fluentbit.io/manual/pipeline/outputs/elasticsearch.

Go to Stack Management->Index patterns->Create index pattern and see the index.

We using fluent bit to pump the cpu metrics and containers log into opensearch. It is based on DaemonSet. If seperate logs is require then  fluent-bit need to configre as a sidecar.

Refer to https://github.com/wenjian80/ociopensearchfluentbit/blob/main/fluent-bit-sc.yaml for example of a side car instead of DaemonSet

if it pure vm refer to fluent bit installation on linux https://docs.fluentbit.io/manual/installation/linux

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opnesearch1.JPG)

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opensearch2.JPG)

![enter image description here](https://github.com/wenjian80/ociopensearchfluentbit/blob/main/opensearchui.JPG)

# Monitoring using cerebro

To configure cerebro

install jdk

download cerebro

configure host

add ws.ssl.loose.acceptAnyCertificate = true under play settings

https://github.com/lmenezes/cerebro/releases/download/v0.9.4/cerebro-0.9.4.zip

# References

https://github.com/fluent

https://github.com/fluent/fluent-bit-kubernetes-logging

https://docs.fluentbit.io/manual/

