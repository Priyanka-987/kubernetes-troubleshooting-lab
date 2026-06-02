# ImagePullBackOff Troubleshooting

## Symptoms

```bash
kubectl get pods
```

Example Output:

```text
nginx-app   0/1   ImagePullBackOff
```

## Investigation

Describe the pod:

```bash
kubectl describe pod nginx-app
```

Check events:

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

Verify image name:

```bash
kubectl get deployment nginx-app -o yaml
```

## Possible Causes

* Incorrect image name
* Incorrect image tag
* Private registry authentication issue
* Registry connectivity issue
* Image does not exist

## Resolution

Update deployment image:

```bash
kubectl set image deployment/nginx-app nginx=nginx:latest
```

Verify:

```bash
kubectl get pods
```

## Lessons Learned

* Verify image names and tags before deployment.
* Configure imagePullSecrets for private registries.
* Test registry connectivity.
