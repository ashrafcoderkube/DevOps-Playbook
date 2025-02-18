
### **AWS Lambda Commands (AWS CLI)**

1. **Install and Configure the AWS CLI:**
   Install AWS CLI and configure it with your credentials:
   ```bash
   aws configure
   ```
   Description: Configures AWS CLI with your access keys, region, and output format.

2. **Create a Lambda Function:**
   Create a Lambda function using the AWS CLI:
   ```bash
   aws lambda create-function \
       --function-name MyLambdaFunction \
       --runtime nodejs18.x \
       --role arn:aws:iam::YOUR_ACCOUNT_ID:role/lambda_basic_execution \
       --handler index.handler \
       --zip-file fileb://function.zip \
       --timeout 30 \
       --memory-size 128
   ```
   Description: Creates a new Lambda function with specified settings, including runtime, handler, role, and timeout.

3. **Update Lambda Function Code:**
   Update the code for an existing Lambda function:
   ```bash
   aws lambda update-function-code \
       --function-name MyLambdaFunction \
       --zip-file fileb://function.zip
   ```
   Description: Updates the Lambda function with new code from the specified ZIP file.

4. **Invoke (Test) a Lambda Function:**
   Test a Lambda function by invoking it with input data:
   ```bash
   aws lambda invoke \
       --function-name MyLambdaFunction \
       --payload '{"key1": "value1", "key2": "value2"}' \
       output.json
   ```
   Description: Invokes the Lambda function with the provided payload and stores the response in `output.json`.

5. **List Lambda Functions:**
   List all the Lambda functions in your account:
   ```bash
   aws lambda list-functions
   ```
   Description: Lists all the Lambda functions in the current AWS account.

6. **Get Lambda Function Configuration:**
   Retrieve configuration details of a Lambda function:
   ```bash
   aws lambda get-function-configuration --function-name MyLambdaFunction
   ```
   Description: Displays detailed configuration information about the specified Lambda function.

7. **Delete a Lambda Function:**
   Delete a Lambda function:
   ```bash
   aws lambda delete-function --function-name MyLambdaFunction
   ```
   Description: Deletes the specified Lambda function from AWS.
