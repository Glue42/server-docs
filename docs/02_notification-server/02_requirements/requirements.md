## Requirements

To run the code:

- Java 11+
- Apache Kafka (recommends latest version or at least 3.0.x)
- Mongo DB (recommends latest version or at least 4.2)

To build the code:

- Java 11+
- (optionally) docker

## Docker

Docker images can be build using `docker` profile i.e. `mvn package -Pdocker`. Once published then you can start full environment executing `docker-compose` up in the `run` folder.