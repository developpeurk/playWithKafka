# PlayWithKafka

This project demonstrates the use of Apache Kafka in a Spring Boot application. It includes components for message production, consumption, and configuration of Kafka topics.

## What is Kafka?

Apache Kafka is a distributed streaming platform designed to handle real-time data feeds with high throughput and fault tolerance. It allows the building of scalable and resilient distributed systems.


## Components

### Producer

The `KafkaProducer` class is responsible for sending messages to a Kafka topic. It utilizes a `KafkaTemplate` to produce messages to the "yassine" topic.

### Consumer

The `KafkaConsumer` class listens to the "yassine" topic within the "myGroup" consumer group. It consumes messages produced to this topic and logs them.


### String Serializer

In Apache Kafka, serializers and deserializers are responsible for converting messages between their original format and bytes for transmission over the Kafka cluster. The `StringSerializer` specifically deals with string-based messages within Kafka.

When a producer sends a string message to a Kafka topic, it needs to be converted into a format suitable for efficient storage and transmission within Kafka. The `StringSerializer` accomplishes this by encoding the string message into a sequence of bytes.

On the consumer side, the `StringDeserializer` performs the reverse operation. It takes the sequence of bytes received from Kafka (which represents a string message) and decodes it back into its original string format.

#### Usage in Kafka Configuration

In the provided Spring configuration (`application.yml` or `application.properties`), these properties specify the serializers and deserializers for string-based messages:

```yaml
spring:
  kafka:
    producer:
      key-serializer: org.apache.kafka.common.serialization.StringSerializer
      value-serializer: org.apache.kafka.common.serialization.StringSerializer
    consumer:
      key-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      value-deserializer: org.apache.kafka.common.serialization.StringDeserializer
````


### REST API

The `MessageController` provides a RESTful endpoint `/api/v1/messages` for sending messages to the Kafka topic. When a POST request is made with a message payload, it uses the `KafkaProducer` to send the message to the "yassine" topic.

## Configuration

The `KafkaTopicConfig` class configures the "yassine" topic using Spring's `TopicBuilder` in the Kafka broker.

The application's Kafka settings are defined in the `application.yml` file under the `spring.kafka` properties. It configures the bootstrap servers, consumer group, serializers, and deserializers for both producers and consumers.

## Usage

1. Start your Kafka broker at `localhost:9092`.
2. Run the application.
3. Use the RESTful endpoint `/api/v1/messages` to send messages to the Kafka topic "yassine".
