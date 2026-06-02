# Ingress Troubleshooting

## Symptoms

Application not accessible through URL.

Example:

```bash
curl http://app.example.com
```

Result:

```text
404 Not Found
```

## Investigation

Check ingress:

```bash
kubectl get ingress
```

Describe ingress:

```bash
kubectl describe ingress app-ingress
```

Check ingress controller:

```bash
kubectl get pods -n ingress-nginx
```

Verify service:

```bash
kubectl get svc
```

## Possible Causes

* Incorrect host configuration
* Incorrect path configuration
* Backend service unavailable
* DNS issue
* Ingress controller issue

## Resolution

Correct ingress rules.

Verify service endpoints:

```bash
kubectl get endpoints
```

Confirm DNS resolution:

```bash
nslookup app.example.com
```

## Lessons Learned

* Validate ingress host and path rules.
* Verify backend services before troubleshooting ingress.
* Check ingress controller logs.

