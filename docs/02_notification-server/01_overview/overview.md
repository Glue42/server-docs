## Overview

Glue42 Notification Server product is an event distribution system built on Java. It consists of a Persistence Server and a Notification Sender service.
It uses MonogDB for persistance and Apache Kafka for comunication between services.

It must be built/plugged in the environment of the client (it is not a shrink-wrapped product in executable code form).

## Architecture

<glue42 name="diagram" image="../../images/notification-server/notification-server-architecture.png">