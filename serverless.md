# serverless

## some serverless services

```
Lambda
SQS
SNS
Api Gateway
DynamoDB
S3
```

## storage options for lambda

```
1. /tmp, lambda layers
2. EFS, S3, etc
```

## lambda Invocation

1. Synchronous - wait for response. from ApiGateway
2. Asynchronous - do not wait for response. from s3

# Dead Letter queue.

send message to sns or sqs for further processing.

# lambda destination

1. SQS, SNS, lambda, Event Bridge
