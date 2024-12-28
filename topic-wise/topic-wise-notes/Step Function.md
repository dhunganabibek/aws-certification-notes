# Step Function

## run serverless application as series of steps

## Each step is task and and whole work flow is state machine

## Type of workflow

```
1. Standard - long running, non idempotent(cause change in state), run at most once.
2. Express - short lived, at least once, idempotent(no side effect: eg reading from s3)
3. Synchronous Express Workflow - wait until it completes
4. Asynchronous Express Workflow - does not wait, have to look cloud log
```
