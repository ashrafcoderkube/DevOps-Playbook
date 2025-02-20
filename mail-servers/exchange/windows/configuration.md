## Exchange Mail Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows Server 2019 or 2022 (Windows Server 2016 may also work but is less optimal).
- **Processor**: 64-bit, 1.4 GHz or faster processor.
- **Memory**: Minimum of 8 GB of RAM; 16 GB or more recommended.
- **Disk Space**: At least 30 GB of available disk space for the Exchange installation.
- **Network**: Stable network connection with DNS and AD (Active Directory) setup.



### **Installation Steps**

### **1. Install the Required Windows Features**
Before installing Exchange, you need to install several Windows features that are required for its operation.

Run the following PowerShell commands to install them:

```powershell
Install-WindowsFeature RSAT-ADDS
Install-WindowsFeature Web-Server
Install-WindowsFeature Web-WebServer
Install-WindowsFeature Web-Mgmt-Console
Install-WindowsFeature Web-Asp-Net
Install-WindowsFeature Web-Net-Ext
Install-WindowsFeature Web-Windows-Auth
```

### **2. Install Microsoft Exchange Server**

- Download the latest version of Exchange Server from the Microsoft website.
- Run the Exchange Server setup executable (`Setup.exe`).
- Follow the on-screen instructions and agree to the terms and conditions.
- Choose the installation type:

    - **Mailbox Role:** Includes Mailbox server, Client Access server, and Transport service.

    - **Edge Transport Role:** Optional for larger environments.

### **3. Post-installation Steps**
After installation, restart the server to complete the process. Then, verify that all Exchange services are running.

Run the following command in PowerShell to check the status of Exchange services:
```sh
Get-Service *exchange*
```


## **Configuration**

### **1. Configure the Exchange Server**
Once installed, you can configure the Exchange Server settings using the Exchange Admin Center (EAC) or PowerShell.

#### Setting up Mailbox Databases

- Open the Exchange Admin Center (EAC) by navigating to `https://<ExchangeServer>/ecp`.

- Configure mailbox databases by going to Servers > Databases and clicking + to create a new database.


#### Configure Email Domains
To configure the email domain, use the following command to add a new domain:

```sh
New-AcceptedDomain -Name "example.com" -DomainName "example.com" -DomainType Authoritative
```

#### Configure Send Connectors
Use this PowerShell command to configure the Send connector:

```sh
New-SendConnector -Name "Outbound Connector" -AddressSpaces "smtp:example.com" -SourceTransportServers "ExchangeServer1"
```


### **How to Use Exchange Mail Server**

#### **1. Create New Mailboxes**
You can create new mailboxes using the Exchange Admin Center or via PowerShell.

To create a new user mailbox via PowerShell:
```sh
New-Mailbox -UserPrincipalName user@example.com -Alias user -Name "User Name" -FirstName "User" -LastName "Name" -Database "Mailbox Database 1"
```

#### **2. Send and Receive Emails**
- **Send Email:** Use Microsoft Outlook or a compatible email client to send and receive emails.

- **Exchange Web Services (EWS):** Programmatically send and receive emails using Exchange Web Services.

To send a test email via PowerShell:
```sh
Send-MailMessage -From "user@example.com" -To "recipient@example.com" -Subject "Test Email" -Body "This is a test email" -SmtpServer "exchange.example.com"
```

#### **3. Monitoring Exchange Server Health**
You can monitor the Exchange Server health by using the `Get-ExchangeServer` and `Test-ServiceHealth` commands:
```sh
Get-ExchangeServer
Test-ServiceHealth
```

#### **4. Backup and Restore Exchange Data**
Use the built-in Exchange Backup and Restore functionality to ensure data redundancy. For example, you can back up mailboxes using the following PowerShell command:
```sh
New-MailboxExportRequest -Mailbox user@example.com -FilePath "\\BackupServer\MailboxBackups\user.pst"
```

