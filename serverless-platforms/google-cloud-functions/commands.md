![GCP](assets/image.png)

## Google Cloud Functions Commands (gcloud CLI)

This document provides a quick reference for common Google Cloud Functions commands using the `gcloud` CLI. Refer to `docs.md` for detailed explanations and usage examples.

### Function Deployment

**Deploys a new Cloud Function. Replace placeholders with your function's details. `--trigger-http` for HTTP-triggered functions.**

```bash
gcloud functions deploy FUNCTION_NAME --runtime RUNTIME --trigger-http --entry-point FUNCTION_ENTRY_POINT --source . --region REGION
```

**Deploys a Cloud Function triggered by a Pub/Sub topic. Replace `TOPIC_NAME` with your topic**

```bash
gcloud functions deploy FUNCTION_NAME --runtime RUNTIME --trigger-topic TOPIC_NAME --entry-point FUNCTION_ENTRY_POINT --source . --region REGION`
```

## Function Configuration

**Sets the memory allocation for a function (e.g., `--memory 256MB`). Must be used in conjunction with deployment**

```bash
gcloud functions deploy FUNCTION_NAME --memory MEMORY_SIZE`
```

**Sets the maximum execution time (timeout) for a function (e.g., `--timeout 60`). Must be used in conjunction with deployment.**

```bash
gcloud functions deploy FUNCTION_NAME --timeout TIMEOUT_SECONDS`
```

## Function Management

**Displays detailed configuration information about a specific Cloud Function.**

```bash
gcloud functions describe FUNCTION_NAME`
```

**Lists all Cloud Functions in a specific Google Cloud region.**

```bash
gcloud functions list --region REGION
```

## ction Invocation

**vokes an HTTP-triggered Cloud Function with the provided JSON data.**

```bash
gcloud functions call FUNCTION_NAME --data '{"key": "value"}'
```

## Fuction Deletion

**Deletes a Cloud Function from a specific Google Cloud region.**

```bash
gcloud functions delete FUNCTION_NAME --region REGION
```

## Other Useful Commands

**Enables the Cloud Functions API for your project (required before deploying functions).**

```bash
gcloud services enable cloudfunctions.googleapis.com
```
