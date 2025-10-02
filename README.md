# Spring Cloud Stream with Apache Kafka

A Spring Boot application demonstrating event-driven messaging with Apache Kafka and Spring Cloud Stream.

## Project Structure

- `controllers`: REST controllers
- `events`: Event models
- `handlers`: Event handlers

## Prerequisites

- Java 8+
- Maven
- Apache Kafka
- ZooKeeper

## Quick Start

1. Start ZooKeeper:
```bash
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

2. Start Kafka:
```bash
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

3. Run the Spring Boot application

## Essential Kafka Commands

### Topic Management

```bash
# Create topic
.\bin\windows\kafka-topics.bat --create --topic R1 --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1

# List topics
.\bin\windows\kafka-topics.bat --list --bootstrap-server localhost:9092

# Describe topic
.\bin\windows\kafka-topics.bat --describe --topic R1 --bootstrap-server localhost:9092
```

### Producer

```bash
.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic R1
```

### Consumer

```bash
# Consume from beginning
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic R1 --from-beginning

# Consume with consumer group
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic R1 --group G1

# List consumer groups
.\bin\windows\kafka-consumer-groups.bat --bootstrap-server localhost:9092 --list

# Describe consumer group
.\bin\windows\kafka-consumer-groups.bat --bootstrap-server localhost:9092 --describe --group G1
```

## Key Concepts

### Consumer Groups
- Same group: Messages are load-balanced (queue behavior)
- Different groups: All groups receive messages (topic behavior)

### Spring Cloud Stream
- **StreamBridge**: Broker-agnostic messaging abstraction
- **KafkaTemplate**: Kafka-specific API with advanced features
- Modes: Consumer, Supplier, Function

## Configuration

See [application.properties](src/main/resources/application.properties) for Kafka broker and topic configuration.
