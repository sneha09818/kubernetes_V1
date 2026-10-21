# Kind Cluster download


## 1. Install kind

```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.33.0/kind-linux-amd64

# For ARM64 (only if uname -m shows aarch64)
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.33.0/kind-linux-arm64

chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

Verify:

```bash
kind version
```

Expected output: `kind v0.33.0 go1.26.7 linux/amd64`

> The line for the other architecture does nothing on your machine. Its `[ ... ]` test fails, so the download is skipped. That is normal.

## 2. Install kubectl

```bash
 sudo snap install kubectl --classic
```

Verify:

```bash
kubectl version --client
```

You should see a `Client Version: v1.xx.x` line. A "cannot connect to server" message is normal until a cluster exists.

## 3. Create a test cluster

```bash
kind create cluster
kubectl get nodes
```

