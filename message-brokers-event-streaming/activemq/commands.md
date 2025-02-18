![activemq](assets/image.png)
### **ActiveMQ Command-Line Tools** 

The ActiveMQ distribution includes several command-line tools located in the `bin/` directory. Below are some commonly used commands:

---

#### **Start and Stop ActiveMQ Broker**

1. **Start the Broker**  
   Starts the ActiveMQ broker:
   ```bash
   bin/activemq start
   ```

2. **Stop the Broker**  
   Stops the ActiveMQ broker:
   ```bash
   bin/activemq stop
   ```

---

#### **JMS Queue and Topic Management**

1. **Create a Queue**  
   Creates a queue for messaging:
   ```bash
   bin/activemq admin createQueue <queue_name>
   ```

2. **Create a Topic**  
   Creates a topic for messaging:
   ```bash
   bin/activemq admin createTopic <topic_name>
   ```

3. **List Queues**  
   Lists all available queues:
   ```bash
   bin/activemq admin listQueues
   ```

4. **List Topics**  
   Lists all available topics:
   ```bash
   bin/activemq admin listTopics
   ```

---

#### **Message Production and Consumption**

1. **Send Message to a Queue**  
   Sends a message to a queue:
   ```bash
   bin/activemq producer --destination <queue_name> --message "<message>"
   ```

2. **Consume Messages from a Queue**  
   Consumes messages from a queue:
   ```bash
   bin/activemq consumer --destination <queue_name>
   ```

3. **Send Message to a Topic**  
   Sends a message to a topic:
   ```bash
   bin/activemq producer --destination <topic_name> --message "<message>"
   ```

4. **Consume Messages from a Topic**  
   Consumes messages from a topic:
   ```bash
   bin/activemq consumer --destination <topic_name>
   ```

---

#### **Broker Management**

1. **Check Broker Status**  
   Checks the status of the broker:
   ```bash
   bin/activemq status
   ```

2. **Show Broker Statistics**  
   Displays broker statistics:
   ```bash
   bin/activemq stats
   ```

3. **Check Broker Health**  
   Monitors the health of the broker:
   ```bash
   bin/activemq healthcheck
   ```

---

#### **Configuration Management**

1. **View Broker Configuration**  
   Views the ActiveMQ configuration (e.g., `activemq.xml`):
   ```bash
   cat conf/activemq.xml
   ```

2. **Reload Configuration**  
   Reloads the configuration file:
   ```bash
   bin/activemq reload
   ```

---

#### **Security and Authentication**

1. **Create User**  
   Adds a new user to the ActiveMQ broker:
   ```bash
   bin/activemq admin createUser --user <username> --password <password>
   ```

2. **Delete User**  
   Deletes a user from the ActiveMQ broker:
   ```bash
   bin/activemq admin deleteUser --user <username>
   ```

---

#### **Log and Troubleshooting**

1. **View Logs**  
   View broker logs to troubleshoot issues:
   ```bash
   tail -f data/activemq.log
   ```

2. **View Debug Logs**  
   View debug-level logs for deeper troubleshooting:
   ```bash
   tail -f data/activemq-debug.log
   ```

---

### **Other ActiveMQ Commands**

1. **Access Web Console**  
   After starting the broker, open a web browser and access the ActiveMQ Web Console:
   ```text
   http://localhost:8161/admin
   ```

   Default username/password:  
   Username: `admin`  
   Password: `admin`  

---

For a more complete list of commands and options, you can refer to the [ActiveMQ Command-Line Reference](https://activemq.apache.org/activemq-5-15-x-documentation).
