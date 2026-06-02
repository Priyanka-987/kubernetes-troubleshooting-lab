# Kubernetes Certificate Expiry Troubleshooting

## Symptoms

Examples:

* Nodes become NotReady
* API server communication issues
* Authentication failures

## Investigation

Check certificate expiration:

```bash
sudo kubeadm certs check-expiration
```

Check kubelet certificate:

```bash
openssl x509 -in /var/lib/kubelet/pki/kubelet-client-current.pem -text -noout
```

## Possible Causes

* Kubernetes certificates expired
* Kubelet certificate expired
* Control plane certificate expired

## Resolution

Renew certificates:

```bash
sudo kubeadm certs renew all
```

Restart services:

```bash
sudo systemctl restart kubelet
```

Verify:

```bash
sudo kubeadm certs check-expiration
```

## Lessons Learned

* Monitor certificate expiration regularly.
* Schedule certificate health checks.
* Renew certificates before expiration.

