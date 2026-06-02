# Node NotReady Troubleshooting

## Symptoms

```bash
kubectl get nodes
```

Output:

```text
worker01    NotReady
```

## Investigation

```bash
kubectl describe node worker01
```

Check:
- Kubelet status
- Disk pressure
- Memory pressure
- Network connectivity

## Root Cause

Kubelet service stopped unexpectedly.

## Resolution

```bash
sudo systemctl restart kubelet
```

Verify:

```bash
kubectl get nodes
```

## Lessons Learned

Monitor kubelet health and node resources.
