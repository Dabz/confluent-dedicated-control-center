# Confluent Dedicated Control Center
## Introduction

This docker-compose template contains a sample configuration to deploy Confluent Control Center (C3) with a dedicated cluster.
It should deploy the following services:

- `zoo` and `kafka`. Simple zookeeper and kafka broker that will be monitored by C3
- `c3_zoo` and `c3_kafka`. C3 dedicated zookeeper and kafka broker instances
- `c3`. Confluent Control Center UI & JVM 

## Usage

```bahs
docker-compose up -d
sleep 10
firefox localhost:9021
```

### Important configuration files
<details>
<summary>Confluent Controler Center properties</summary>
<pre>
bootstrap.servers=c3_kafka:9092
zookeeper.connect=c3_zoo:2181
</pre>
</details>

<details>
<summary>Application Apache Kafka Broker</summary>
<pre>
confluent.metrics.reporter.bootstrap.servers=c3_kafka:9092
metric.reporters=io.confluent.metrics.reporter.ConfluentMetricsReporter
</pre>
</details>
