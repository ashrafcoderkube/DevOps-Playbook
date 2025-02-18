
![nats](https://upload.wikimedia.org/wikipedia/en/4/4c/NATS_logo.svg)

## NATS Commands (Quick Reference)

This document provides a quick reference for commonly used NATS commands. For detailed explanations, setup instructions, and configuration options, consult the `docs.md` file.

---

### **Basic Messaging**

#### Publishes a message to a subject.

```bash
nats pub <subject> <message>
```

Publishes a message to the specified subject. Use this command to send data between publishers and subscribers.

#### Subscribes to a subject.

```bash
nats sub <subject>
```

Subscribes to the specified subject to receive messages. The client listens for incoming messages on this subject.

---

### **Request-Reply**

#### Sends a request and waits for a reply.

```bash
nats req <subject> <message>
```

Sends a request to the specified subject and waits for a reply. This is used in scenarios where the sender expects a response.

---

### **JetStream (if enabled)**

#### Adds a stream with a subject.

```bash
nats stream add <stream_name> --subjects=<subject>
```

Creates a JetStream stream with a specified subject. This command enables the stream to persist messages based on the subject.

#### Lists all streams.

```bash
nats stream list
```

Lists all the active JetStream streams in the server. Helps to view the available streams for consumption.

#### Purges messages from a stream.

```bash
nats stream purge <stream_name>
```

Purges all messages from a specific stream. Useful for clearing out old messages from a stream.

#### Deletes a stream.

```bash
nats stream delete <stream_name>
```

Deletes the specified stream. All associated messages will be removed from storage.

---

### **Cluster Management**

#### Displays status of the NATS server in a cluster.

```bash
nats server status
```

Shows the status of the NATS server, including whether it’s part of a cluster, its health, and other metrics.

#### Lists the servers in the NATS cluster.

```bash
nats cluster info
```

Displays information about the servers in the current NATS cluster. This is useful for debugging cluster-related issues.

---

### **Authorization & Security**

#### Add a user with authentication.

```bash
nats account add <username> --password <password>
```

Adds a new user to the NATS server with authentication details. Ensure that you configure secure access for clients.

#### Set permissions for a user.

```bash
nats account permissions <username> --allow <subject> --deny <subject>
```

Sets the permissions for a specific user, allowing or denying access to certain subjects. Use this to restrict or grant access.

#### Generate a token for secure authentication.

```bash
nats account generate-token <username>
```

Generates a secure token for the user’s authentication with the NATS server. This is typically used for API access.

---

### **Performance Monitoring**

#### Displays server statistics.

```bash
nats server stats
```

Displays important server metrics such as the number of active clients, the number of messages published, and memory usage.

#### Displays connection information.

```bash
nats connection info
```

Shows detailed information about the client’s connection to the NATS server, such as latency and uptime.

---

### **Troubleshooting**

#### Check for active subscriptions.

```bash
nats sub list
```

Lists all active subscriptions on the NATS server. Helps in identifying potential issues in message delivery.

#### Check logs for errors.

```bash
nats log tail
```

Tails the NATS server logs to monitor for any potential issues or errors. Useful during debugging.

#### Get detailed connection logs.

```bash
nats connection logs <connection_id>
```

Retrieves detailed logs for a specific connection, providing insights into the interaction between clients and the server.

---

### **Advanced Commands**

#### Stream message details.

```bash
nats stream info <stream_name>
```

Displays information about the specified JetStream stream, such as the number of messages, storage, and configuration details.

#### Subscribes to a subject with durable state.

```bash
nats sub <subject> --durable <consumer_name>
```

Subscribes to a subject while maintaining the consumer state. Useful for ensuring that messages are not missed if the consumer disconnects.

#### Acknowledges a message.

```bash
nats ack <message_id>
```

Acknowledges that a message has been processed successfully. Required when using message queues and guarantees reliable message delivery.

---

### **General Server Management**

#### Start the NATS server with a specific configuration.

```bash
nats-server -c <config_file>
```

Starts the NATS server with a specified configuration file. This allows the user to configure advanced options like clustering, TLS, and authorization.

#### Restart the NATS server.

```bash
nats-server restart
```

Restarts the NATS server. Useful for applying changes in configuration without shutting down the service.

---

### **Additional Resources**

For more detailed usage and advanced topics, refer to the official NATS documentation:

* [NATS Documentation](https://docs.nats.io/)
* [NATS JetStream Guide](https://docs.nats.io/nats-concepts/jetstream/)
* [NATS GitHub Repository](https://github.com/nats-io/nats-server)

