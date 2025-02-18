![azure](assets/image.png)

**Creates a new Function App.**

```bash
az functionapp create --name <function_app_name> --storage-account <storage_account_name> --resource-group <resource_group_name> --consumption-plan-location <location> --runtime <runtime>
```

**Lists Function Apps in a resource group.**

```bash
az functionapp list --resource-group <resource_group_name>
```

**Lists application settings (environment variables).**

```bash
az functionapp config appsettings list --name <function_app_name> --resource-group <resource_group_name>
```

**Sets application settings.**

```bash
az functionapp config appsettings set --name <function_app_name> --resource-group <resource_group_name> --settings "setting1=value1" "setting2=value2"
```

**Deletes a Function App.**

```bash
az functionapp delete --name <function_app_name> --resource-group <resource_group_name>
```

---

**Function Deployment (Azure Functions Core Tools)**

**Deploys function code to an Azure Function App. Execute this from your function app's root directory.**

```bash
func azure functionapp publish <function_app_name>
```

---

**Local Development (Azure Functions Core Tools)**

**Initializes a new function project in the current directory.**

```bash
func init
```

**Creates a new function within a project, prompting for a template and trigger.**

```bash
func new
```

**Starts the Azure Functions runtime locally for testing.**

```bash
func start
```

**Starts the function host locally for testing. This is an alias for `func start`.**

```bash
func host start
```
