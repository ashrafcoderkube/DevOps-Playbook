![azure](assets/image.png)

## Azure Functions

### **Overview**

Azure Functions is a serverless compute service that enables you to run event-triggered code without explicitly provisioning or managing infrastructure. You can use Azure Functions to build APIs, process data, integrate systems, and respond to IoT events. Azure Functions supports a variety of programming languages, and you pay only for the compute time your code consumes.

### **Key Features**

*   **Serverless:** No infrastructure management, patching, or scaling required.
*   **Event-Driven:** Functions are triggered by a wide range of event sources, including HTTP requests, timers, queues, databases, and more.
*   **Automatic Scaling:** Azure Functions automatically scales to handle incoming load, ensuring optimal performance.
*   **Multiple Language Support:** Supports C#, F#, Java, JavaScript, Python, PowerShell, and more.
*   **Pay-Per-Use:** You pay only for the resources consumed when your function is running. Consumption plan and Premium plan options available.
*   **Integration with Azure Services:** Integrates seamlessly with Azure Blob Storage, Azure Queue Storage, Azure Event Hubs, Azure Cosmos DB, and other Azure services.
*   **Triggers and Bindings:** Uses triggers to start execution and bindings to simplify connecting to data sources and services.
*   **Container Image Support:** You can deploy container images as Azure Functions for custom dependencies and configurations.

### **Use Cases**

*   **API Development:** Build REST APIs and microservices using HTTP triggers.
*   **Data Processing:** Process data from Azure Blob Storage, Azure Queue Storage, and other data sources.
*   **Event Handling:** React to events in Azure Event Hubs, Azure Service Bus, and other event-driven systems.
*   **Webhooks:** Process incoming webhooks from third-party services.
*   **IoT Backends:** Process data from IoT devices.
*   **Scheduled Tasks:** Implement scheduled tasks using timer triggers.

### **Setting Up Azure Functions**

1.  **Prerequisites:**
    *   An Azure subscription.
    *   The Azure CLI installed and configured.
    *   The Azure Functions Core Tools installed.
    *   A resource group in Azure to contain your function app.

2.  **Install the Azure CLI:**

    *   Follow the instructions on the Microsoft Azure documentation to install the Azure CLI: [https://docs.microsoft.com/en-us/cli/azure/install](https://docs.microsoft.com/en-us/cli/azure/install)

3.  **Install the Azure Functions Core Tools:**

    *   The Azure Functions Core Tools provide a local development environment for creating and testing Azure Functions.
        Follow the instructions on the Microsoft Azure documentation to install: [https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local)

4.  **Create a Resource Group (if you don't have one):**

    ```azurecli
    az group create --name <resource_group_name> --location <location>
    ```

    *   Replace `<resource_group_name>` with the name of your resource group.
    *   Replace `<location>` with the Azure region (e.g., `eastus`, `westeurope`).

5.  **Create a Storage Account (required by Azure Functions):**

    ```azurecli
    az storage account create --name <storage_account_name> --location <location> --resource-group <resource_group_name> --sku Standard_LRS
    ```

    *   Replace `<storage_account_name>` with a unique name for your storage account.
    *   Replace `<location>` with the Azure region.
    *   Replace `<resource_group_name>` with the name of your resource group.

6.  **Create a Function App:**

    ```azurecli
    az functionapp create --name <function_app_name> --storage-account <storage_account_name> --resource-group <resource_group_name> --consumption-plan-location <location> --runtime <runtime>
    ```

    *   Replace `<function_app_name>` with a unique name for your function app.
    *   Replace `<storage_account_name>` with the name of your storage account.
    *   Replace `<resource_group_name>` with the name of your resource group.
    *   Replace `<location>` with the Azure region.
    *   Replace `<runtime>` with the runtime environment (e.g., `dotnet`, `node`, `python`).  Use `node` for JavaScript functions.

---

### **Azure Functions Commands (Azure CLI)**

1.  **Create a Function App:**

    ```azurecli
    az functionapp create --name <function_app_name> --storage-account <storage_account_name> --resource-group <resource_group_name> --consumption-plan-location <location> --runtime <runtime>
    ```

    Creates a new function app in Azure.

2.  **Deploy Function Code:**

    ```azurecli
    func azure functionapp publish <function_app_name>
    ```

    Deploys your function code to the Azure Function App.  This command is executed from the root directory of your function project (where `host.json` is located) using the `func` command-line tool, a part of Azure Functions Core Tools.

3.  **List Function Apps:**

    ```azurecli
    az functionapp list --resource-group <resource_group_name>
    ```

    Lists all function apps in a specific resource group.

4.  **Get Function App Settings:**

    ```azurecli
    az functionapp config appsettings list --name <function_app_name> --resource-group <resource_group_name>
    ```

    Lists the application settings for a function app.

5.  **Update Function App Settings:**

    ```azurecli
    az functionapp config appsettings set --name <function_app_name> --resource-group <resource_group_name> --settings "setting1=value1" "setting2=value2"
    ```

    Sets application settings for a function app.  Use this to configure environment variables.

6.  **Delete a Function App:**

    ```azurecli
    az functionapp delete --name <function_app_name> --resource-group <resource_group_name>
    ```

    Deletes a function app from Azure.

---

### **Example Azure Function Code**

#### JavaScript (Node.js) - `index.js`

```javascript
module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');

    const name = (req.query.name || (req.body && req.body.name));
    const responseMessage = name
        ? "Hello, " + name + ". Welcome to Azure Functions!"
        : "This HTTP triggered function executed successfully. Pass a name in the query string or in the request body for a personalized response.";

    context.res = {
        // status: 200, /* Defaults to 200 */
        body: responseMessage
    };
}
content_copy
download
Use code with caution.
Markdown

Explanation: This JavaScript function responds to HTTP requests, extracting a "name" parameter from the query string or request body and returning a personalized greeting.

Python - __init__.py
import logging

import azure.functions as func


def main(req: func.HttpRequest) -> func.HttpResponse:
    logging.info('Python HTTP trigger function processed a request.')

    name = req.params.get('name')
    if not name:
        try:
            req_body = req.get_json()
        except ValueError:
            pass
        else:
            name = req_body.get('name')

    if name:
        return func.HttpResponse(
             f"Hello, {name}. Welcome to Azure Functions!",
             status_code=200
        )
    else:
        return func.HttpResponse(
             "Please pass a name on the query string or in the request body",
             status_code=400
        )   
```

