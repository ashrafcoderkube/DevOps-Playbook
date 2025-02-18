

![rabbitmq](assets/image.png)

## Apache Kafka

### **Overview**

Apache Kafka is a distributed, fault-tolerant, high-throughput streaming platform designed to handle large-scale, real-time data processing. Kafka is widely used for building real-time data pipelines, message queues, and stream-processing applications. It is designed to handle massive amounts of data with low latency and high availability.

Kafka is composed of producers, brokers, consumers, and topics, which work together to provide a highly scalable, fault-tolerant solution for streaming data.

### **Key Features**

*   **Distributed:** Kafka runs as a cluster, distributing data and load across multiple brokers to ensure scalability and fault tolerance.
*   **Scalable:** Kafka clusters can be easily expanded by adding more brokers to handle increasing data volumes, ensuring horizontal scaling.
*   **Fault-Tolerant:** Kafka ensures high availability and data durability by replicating data across multiple brokers. If a broker fails, another broker in the cluster can take over.
*   **High-Throughput:** Kafka is optimized for high throughput, capable of handling millions of messages per second for both reads and writes.
*   **Persistent Storage:** Kafka stores data on disk, making it durable and allowing consumers to read messages at their own pace, even after they’ve been produced.
*   **Stream Processing:** Kafka supports stream processing through Kafka Streams API and integration with other stream processing frameworks like Apache Flink and Apache Spark.
*   **Time-Based Retention:** Kafka allows data retention based on configurable time or size, enabling control over the retention period for messages in topics.

### **Use Cases**

*   **Real-time Data Pipelines:** Kafka is used to create efficient data pipelines that enable the movement of data between systems in real time.
*   **Stream Processing Applications:** Kafka is ideal for building applications that need to process data in real time, such as fraud detection, anomaly detection, and real-time analytics.
*   **Log Aggregation:** Kafka aggregates log data from different sources, such as application servers or IoT devices, and provides a reliable message queue for processing or storing logs.
*   **Metrics Collection:** Kafka helps collect metrics from systems, applications, or services in real time for monitoring and analytics purposes.
*   **Event Sourcing:** Kafka is commonly used for event-driven architectures, where events are logged and can be replayed as needed for data consistency or to build event-driven systems.

### **Setting Up Kafka**

1. **Prerequisites:**
    *   **Java Development Kit (JDK)** version 8 or higher must be installed, as Kafka is written in Java and requires JDK for execution.
    *   **ZooKeeper** must be installed to manage the Kafka cluster’s metadata and coordination.

2. **Install ZooKeeper** (Example using apt on Debian/Ubuntu):
   
    Kafka relies on Apache ZooKeeper for cluster management and coordination. Follow the steps to install ZooKeeper before installing Kafka.

    ```bash
    sudo apt update && sudo apt install zookeeperd
    ```

3. **Download Kafka:**

    You can download the latest version of Apache Kafka from the official Apache website.

    *   Visit [Kafka Download Page](https://kafka.apache.org/downloads).
    *   Select the version you want to download and extract the Kafka tar file.

4. **Extract Kafka:**

    After downloading Kafka, extract the contents and navigate to the Kafka directory:

    ```bash
    tar -xzf kafka_<scala_version>-<kafka_version>.tgz
    cd kafka_<scala_version>-<kafka_version>
    ```

5. **Configure Kafka:**

    *   Kafka’s configuration file `config/server.properties` allows you to adjust several settings. Below are some key configuration options:
        *   **broker.id:** The unique identifier for each broker in the Kafka cluster. Each broker in the cluster must have a distinct `broker.id`.
        *   **listeners:** The address and port Kafka listens on for incoming connections (e.g., `PLAINTEXT://localhost:9092`).
        *   **zookeeper.connect:** The ZooKeeper connection string, pointing to the ZooKeeper server (e.g., `localhost:2181`).
        *   **log.dirs:** The directory on the filesystem where Kafka will store its log files (messages).

    Example `server.properties` configuration:
    ```bash
    broker.id=1
    listeners=PLAINTEXT://localhost:9092
    zookeeper.connect=localhost:2181
    log.dirs=/var/lib/kafka/logs
    ```

6. **Start ZooKeeper:**

    Ensure ZooKeeper is running before starting Kafka. Start ZooKeeper using:

    ```bash
    sudo systemctl start zookeeper
    ```

7. **Start Kafka:**

    After ZooKeeper is running, you can start the Kafka server using the following command:

    ```bash
    bin/kafka-server-start.sh config/server.properties
    ```

    Kafka will now be running, and you can interact with it using the Kafka command-line tools.

### **Kafka Command-Line Tools**

Kafka provides a set of command-line tools to help you manage topics, produce and consume messages, and configure your Kafka cluster. These tools are located in the `bin/` directory.

---

#### **Creating Topics:**

Create a new topic where messages can be produced and consumed.

```bash
bin/kafka-topics.sh --create --topic <topic_name> --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

This creates a topic with the specified number of partitions and replication factor.

#### **Listing Topics:**

List all the available topics in the Kafka cluster.

```bash
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

#### **Producing Messages:**

Start a producer that will publish messages to a specified topic.

```bash
bin/kafka-console-producer.sh --topic <topic_name> --bootstrap-server localhost:9092
```

This will allow you to input messages, and they will be sent to the specified Kafka topic.

#### **Consuming Messages:**

Start a consumer to read messages from a specified topic.

```bash
bin/kafka-console-consumer.sh --topic <topic_name> --bootstrap-server localhost:9092 --from-beginning
```

This command will display the messages produced to the specified topic.

---

### **Important Configuration Notes**

*   **Broker IDs:** Ensure each broker in your Kafka cluster has a unique `broker.id`. This is essential for proper identification and communication between brokers in the cluster.
*   **Listeners:** Configure the `listeners` property correctly to allow clients to connect to the Kafka broker. You can have multiple listeners (e.g., for both plaintext and SSL communication).
*   **ZooKeeper:** Kafka relies on ZooKeeper for cluster coordination. Ensure that the `zookeeper.connect` configuration is correctly set to the address of the ZooKeeper server.
*   **Replication:** Kafka supports data replication across brokers. Set the `default.replication.factor` in the server properties to ensure that data is replicated across multiple brokers for fault tolerance.
*   **Log Retention:** Configure log retention policies in `log.retention.hours` or `log.retention.bytes` to manage the size and duration of data stored in Kafka topics.

---

### **Troubleshooting**

*   **Connection Issues:** Ensure both Kafka and ZooKeeper are running and accessible. Check the firewall or network issues that may prevent connections.
*   **Broker ID Conflicts:** If multiple brokers have the same `broker.id`, the Kafka cluster may fail to start. Verify that each broker in the cluster has a unique ID.
*   **ZooKeeper Errors:** If ZooKeeper is not running or misconfigured, Kafka will fail to start. Ensure that the `zookeeper.connect` setting is correct and that ZooKeeper is running.

---

### **Additional Resources**

For more detailed usage and advanced topics, refer to the official Kafka documentation:

* [Apache Kafka Documentation](https://kafka.apache.org/documentation/)
* [Kafka Quickstart Guide](https://kafka.apache.org/quickstart)
* [Kafka GitHub Repository](https://github.com/apache/kafka)
