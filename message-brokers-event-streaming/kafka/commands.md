

![rabbitmq](assets/image.png)

## Apache Kafka Commands (Quick Reference)

This document provides a quick reference for Kafka commands. For detailed explanations, setup instructions, and configuration options, consult the `docs.md` file.

---

### **Topic Management**

#### **Creates a New Topic**

```bash
bin/kafka-topics.sh --create --bootstrap-server <broker_list> --topic <topic_name> --partitions <num_partitions> --replication-factor <num_replicas>
```
- **`--create`**: Creates a new Kafka topic.
- **`--bootstrap-server <broker_list>`**: The list of Kafka brokers to connect to (e.g., `localhost:9092`).
- **`--topic <topic_name>`**: The name of the new topic.
- **`--partitions <num_partitions>`**: The number of partitions for the topic (higher partitions allow higher parallelism).
- **`--replication-factor <num_replicas>`**: The number of replicas for the topic (ensure there are enough brokers for replication).

#### **Lists Existing Topics**

```bash
bin/kafka-topics.sh --list --bootstrap-server <broker_list>
```
- **`--list`**: Lists all available topics in the Kafka cluster.
- **`--bootstrap-server <broker_list>`**: The list of Kafka brokers (e.g., `localhost:9092`).

#### **Describe Topic Details**

```bash
bin/kafka-topics.sh --describe --bootstrap-server <broker_list> --topic <topic_name>
```
- **`--describe`**: Describes the details of the specified topic (e.g., partition details, leader brokers, replicas).
- **`--topic <topic_name>`**: The topic you want to describe.

#### **Delete Topic**

```bash
bin/kafka-topics.sh --delete --bootstrap-server <broker_list> --topic <topic_name>
```
- **`--delete`**: Deletes the specified topic from the Kafka cluster.
- **Note**: Topic deletion may need to be enabled by setting `delete.topic.enable=true` in the `server.properties` file.

---

### **Message Production**

#### **Starts a Console Producer**

```bash
bin/kafka-console-producer.sh --bootstrap-server <broker_list> --topic <topic_name>
```
- **`--bootstrap-server <broker_list>`**: The list of Kafka brokers (e.g., `localhost:9092`).
- **`--topic <topic_name>`**: The topic where the producer will send messages.

This command allows you to type messages directly into the terminal, and they will be sent to the Kafka topic.

#### **Send a Message to a Topic from a File**

```bash
bin/kafka-console-producer.sh --bootstrap-server <broker_list> --topic <topic_name} < <file_name>
```
- **`<file_name>`**: Path to the file from which messages will be read and sent to the specified Kafka topic.

---

### **Message Consumption**

#### **Starts a Console Consumer**

```bash
bin/kafka-console-consumer.sh --bootstrap-server <broker_list> --topic <topic_name> --from-beginning
```
- **`--from-beginning`**: Consumes messages from the beginning of the topic (i.e., even old messages).
- **`--bootstrap-server <broker_list>`**: The list of Kafka brokers (e.g., `localhost:9092`).
- **`--topic <topic_name>`**: The topic to consume messages from.

#### **Consume Messages from a Specific Offset**

```bash
bin/kafka-console-consumer.sh --bootstrap-server <broker_list> --topic <topic_name> --offset <offset_number> --partition <partition_number>
```
- **`--offset <offset_number>`**: Start consuming from a specific offset within the partition.
- **`--partition <partition_number>`**: Specify which partition to consume messages from.

#### **Consume Messages with a Limit**

```bash
bin/kafka-console-consumer.sh --bootstrap-server <broker_list> --topic <topic_name> --max-messages <number_of_messages>
```
- **`--max-messages <number_of_messages>`**: Consume a specified number of messages and stop.

---

### **Message Production & Consumption in a Batch**

#### **Produce Messages in Batch (using a File)**

```bash
bin/kafka-console-producer.sh --bootstrap-server <broker_list> --topic <topic_name} < <file_name>
```
- **`<file_name>`**: Path to the file that contains multiple lines of messages to be sent to the specified Kafka topic in a batch.

#### **Consume and Process Multiple Topics**

```bash
bin/kafka-console-consumer.sh --bootstrap-server <broker_list> --topic <topic_1>,<topic_2> --from-beginning
```
- **`--topic <topic_1>,<topic_2>`**: Consume messages from multiple topics at the same time. 

---

### **Consumer Group Management**

#### **Create Consumer Group**

Kafka allows consumers to group together and share the consumption of topics, where each consumer in a group reads from a unique partition.

```bash
bin/kafka-consumer-groups.sh --bootstrap-server <broker_list> --create --group <consumer_group_name> --topic <topic_name>
```
- **`--create`**: Creates a new consumer group.
- **`--group <consumer_group_name>`**: The name of the consumer group.
- **`--topic <topic_name>`**: The topic associated with the consumer group.

#### **Describe Consumer Group**

```bash
bin/kafka-consumer-groups.sh --bootstrap-server <broker_list> --describe --group <consumer_group_name>
```
- **`--describe`**: Describes the status and consumption details of a specific consumer group.
- **`--group <consumer_group_name>`**: The consumer group whose status you want to inspect.

#### **List Consumer Groups**

```bash
bin/kafka-consumer-groups.sh --bootstrap-server <broker_list> --list
```
- **`--list`**: Lists all consumer groups in the Kafka cluster.

---

### **Cluster Management**

#### **Check Broker Status**

```bash
bin/kafka-broker-api-versions.sh --bootstrap-server <broker_list>
```
- **`--broker-api-versions`**: Displays the API versions supported by the broker and verifies that the broker is running and reachable.

#### **Check Cluster Metadata**

```bash
bin/kafka-metadata-shell.sh --bootstrap-server <broker_list>
```
- **`--metadata`**: Displays metadata related to topics, brokers, and partitions.

---

### **Additional Operations**

#### **List Consumer Lag**

```bash
bin/kafka-consumer-groups.sh --bootstrap-server <broker_list> --describe --group <consumer_group_name>
```
- **`--describe`**: Shows the consumer lag (how far behind a consumer is) for a specific consumer group.

#### **Reassign Partitions**

```bash
bin/kafka-reassign-partitions.sh --bootstrap-server <broker_list> --reassignment-json-file <file_name> --execute
```
- **`--reassignment-json-file <file_name>`**: A JSON file that defines the partition reassignment, where you specify which partitions should be moved to different brokers.

#### **Update Log Retention Policy**

```bash
bin/kafka-configs.sh --bootstrap-server <broker_list> --entity-type topics --entity-name <topic_name> --alter --add-config retention.ms=<retention_time>
```
- **`--add-config retention.ms=<retention_time>`**: Alters the retention time for the specified topic, in milliseconds.

---

### **Important Notes**

- **`--bootstrap-server <broker_list>`**: A list of broker addresses (e.g., `localhost:9092`) used to connect to the Kafka cluster.
- **`--topic <topic_name>`**: Specifies the topic to interact with.
- **`--group <consumer_group_name>`**: The consumer group name for Kafka consumers.

