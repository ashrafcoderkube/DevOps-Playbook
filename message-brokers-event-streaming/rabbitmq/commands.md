![rabbitmq](assets/image.png)
## RabbitMQ Commands (`rabbitmqctl` - Quick Reference)

This document provides a quick reference for RabbitMQ management using `rabbitmqctl`. For detailed explanations, security considerations, and setup instructions, consult the `docs.md` file.

**Server Status**

*   `sudo rabbitmqctl status`: Checks the RabbitMQ server status.

**Queue Management**

*   `sudo rabbitmqctl list_queues`: Lists all queues.

**User Management**

*   `sudo rabbitmqctl add_user <username> <password>`: Adds a new user.
*   `sudo rabbitmqctl set_permissions -p / <username> ".*" ".*" ".*"`: Sets permissions for a user on the default virtual host.
*   `sudo rabbitmqctl set_user_tags <username> administrator`: Grants administrator privileges to a user.
*   `sudo rabbitmqctl delete_user <username>`: Deletes a user.

**Virtual Host Management**

*   `sudo rabbitmqctl add_vhost <vhost_name>`: Creates a new virtual host.
*   `sudo rabbitmqctl delete_vhost <vhost_name>`: Deletes a virtual host.