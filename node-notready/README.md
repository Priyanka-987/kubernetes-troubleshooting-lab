# Node NotReady Troubleshooting

## Symptoms

Check node status:

```bash
kubectl get nodes
```

Example Output:

```text
NAME       STATUS     ROLES           AGE   VERSION
worker01   NotReady   <none>          10d   v1.30.0
```

## Investigation

### Check Node Details

```bash
kubectl describe node worker01
```

### Check Kubelet Status

```bash
sudo systemctl status kubelet
```

### Check Kubelet Logs

```bash
sudo journalctl -u kubelet -n 50
```

### Check Node Conditions

```bash
kubectl describe node worker01 | grep -A5 Conditions
```

## Possible Causes

- Kubelet service stopped
- Network connectivity issue
- Disk pressure
- Memory pressure
- Certificate issue
- Container runtime issue

## Resolution

Restart kubelet:

```bash
sudo systemctl restart kubelet
```

Verify node status:

```bash
kubectl get nodes
```

Expected Output:

```text
NAME       STATUS   ROLES           AGE   VERSION
worker01   Ready    <none>          10d   v1.30.0
```

## Lessons Learned

- Monitor node health regularly.
- Check kubelet status as an initial troubleshooting step.
- Review node conditions to identify resource-related issues.
- Verify container runtime and network connectivity.
```
