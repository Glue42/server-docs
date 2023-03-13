## Overview

The Glue42 metrics are published as structured JSON trees. Once published to a server, they are transformed and routed to the respective storage (or to another transport bus, depending on the client infrastructure and intentions). The transformation is done using the [JSLT](https://github.com/schibsted/jslt) language. The fields in the JSON files are queried and if they meet certain requirements, the metrics are routed to the respective storage/bus.

Glue42 provides solutions for metrics transformation depending on the respective storage and data volumes: [Metrics Server](#metrics_server) - for lower record volumes, and [Metrics Advanced Server](#metrics_advanced_recorder) - for large record volumes. Also available is a [Metrix in a Box](#metrics_server-metrics_in_a_box) solution which includes the Metrics Server connected with a preconfigured SQL database and allows clients to quickly connect an analytics tool of their choice in order to evaluate the Metrics Server.

Currently, storage support is offered for RDBMS, ElasticSearch and VaranDB (Tick42 proprietary Cassandra/ElasticSearch high-volume solution). Support for other options is being developed as well.

## Metrics Server

The Metrics Server is a server-side component combining a REST and a transformation service. It can receive metrics via a REST protocol, Kafka and Solace. The Metrics Server transforms the Glue42 metrics allowing for direct storage in SQL databases. Clients can also insert custom code to write to any data store of their choice. The Metrics server is a solution suitable for lower record volumes. The actual volumes depend on the number of metrics and the capacity of the SQL database, but the Metrics Server can handle hundreds of desktops.

<glue42 name="diagram" image="../../images/metrics-server/metrics-server.png">

### Metrics in a Box

The Metrics in a Box solution allows developers to easily setup and evaluate the [Metrics Server](#transformation_and_storage-metrics_server). It comes as two docker images that contain the Metrics Server and an SQL database. The SQL database is preconfigured with tables which store some of the default Glue42 metrics. The Metrics Server transforms the metrics so that they can be used in these tables. Based on this setup, users can connect an analytics software of their choice (e.g., Tableau or Qlik) to the SQL database.

<glue42 name="diagram" image="../../images/metrics-server/metrics-in-a-box.png">

## Metrics Advanced Server

The Metrics Advanced Server is a Glue42 Java app based on the Tick42 proprietary VaranDB library. The Metrics Advanced Server can transform large volumes of metrics (from tens of thousands of users) and store them using Cassandra and ElasticSearch storage engines. Supported transports are REST API, Kafka, Solace. A site-specific data extraction process is required to extract the data from the Cassandra/ElasticSearch store and use it for reports. Typically, this involves writing the extracted data to an SQL store for use by a business intelligence system.

<glue42 name="diagram" image="../../images/metrics-server/metrics-recorder.png">