<img src="assets/image.png" alt="envoy" width="150" >

### **AWS API Gateway CLI Commands**

1. **Create a REST API**
   This command creates a new REST API in API Gateway.

   ```bash
   aws apigateway create-rest-api --name <api_name> --description "<description>" --region <region>
   ```

2. **Get a List of APIs**
   Retrieves all the REST APIs in your account.

   ```bash
   aws apigateway get-rest-apis --region <region>
   ```

3. **Create a Resource**
   Creates a new resource (such as a URL path) for the specified API.

   ```bash
   aws apigateway create-resource --rest-api-id <api_id> --parent-id <parent_resource_id> --path-part <resource_path> --region <region>
   ```

4. **Create a Method**
   Creates a new method (GET, POST, PUT, DELETE, etc.) for a specified resource in the API.

   ```bash
   aws apigateway put-method --rest-api-id <api_id> --resource-id <resource_id> --http-method <http_method> --authorization-type NONE --region <region>
   ```

5. **Deploy an API**
   Deploys a version of the API to a specified stage.

   ```bash
   aws apigateway create-deployment --rest-api-id <api_id> --stage-name <stage_name> --region <region>
   ```

6. **Create an API Key**
   Creates an API key for accessing the API.

   ```bash
   aws apigateway create-api-key --name <api_key_name> --enabled --region <region>
   ```

7. **Create Usage Plan**
   A usage plan controls how API keys can access your API.

   ```bash
   aws apigateway create-usage-plan --name <usage_plan_name> --description "<description>" --api-stages apiId=<api_id>,stage=<stage_name> --region <region>
   ```

8. **Associate API Key with Usage Plan**
   Associates an API key with a usage plan to allow access.

   ```bash
   aws apigateway create-usage-plan-key --usage-plan-id <usage_plan_id> --key-id <api_key_id> --key-type API_KEY --region <region>
   ```

9. **Enable Caching for API Gateway**
   Enable response caching to reduce latency for repeated requests.

   ```bash
   aws apigateway update-stage --rest-api-id <api_id> --stage-name <stage_name> --cache-cluster-enabled --cache-cluster-size <size> --region <region>
   ```

10. **Enable Access Logging**
    Enable logging for your API to track request and response logs.

    ```bash
    aws apigateway update-stage --rest-api-id <api_id> --stage-name <stage_name> --access-log-settings format=<log_format>,destination-arn=<log_group_arn> --region <region>
    ```

11. **Delete an API**
    Deletes a REST API from API Gateway.

    ```bash
    aws apigateway delete-rest-api --rest-api-id <api_id> --region <region>
    ```

12. **Get the API Keys**
    List the API keys that have been created in your account.

    ```bash
    aws apigateway get-api-keys --region <region>
    ```

13. **List API Resources**
    List all resources for a specific API.

    ```bash
    aws apigateway get-resources --rest-api-id <api_id> --region <region>
    ```

14. **Test the API**
    You can use `curl` or Postman for testing, but here’s a basic `curl` example to invoke an API:

    ```bash
    curl -X GET "<api_url>/resource" -H "x-api-key: <api_key>"
    ```

### **Links to Official Documentation**

- [AWS API Gateway CLI Documentation](https://docs.aws.amazon.com/cli/latest/reference/apigateway/index.html)
- [API Gateway REST API Reference](https://docs.aws.amazon.com/apigateway/latest/api-reference/)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/)
