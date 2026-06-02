# CrashLoopBackOff Troubleshooting

## Symptoms

```bash
kubectl get pods
```

Example Output:

```text
web-app   0/1   CrashLoopBackOff
```

## Investigation

Check logs:

```bash
kubectl logs web-app
```

Check previous container logs:

```bash
kubectl logs web-app --previous
```

Describe pod:

```bash
kubectl describe pod web-app
```

## Possible Causes

* Application startup failure
* Configuration error
* Missing ConfigMap
* Missing Secret
* Resource limits exceeded

## Resolution

Review application logs and configuration.

Verify ConfigMaps:

```bash
kubectl get configmap
```

Verify Secrets:

```bash
kubectl get secrets
```

Redeploy after fixing configuration.

## Lessons Learned

* Review application logs first.
* Validate application configuration before deployment.
* Monitor restart counts.

