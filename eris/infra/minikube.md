## Prerequisites

Before installing Minikube, the system must meet the following minimum requirements:

* **CPU:**  4 cores or more (8 recommended for HA setups)
* **RAM:**  8 GB minimum
* **Disk:**  20 GB of free space
* **Internet:**  A stable connection
* A non‑root **user** with `sudo`

## Update Debian and base tools

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt install -y curl wget ca-certificates gnupg lsb-release apt-transport-https
```


---

## Install Docker Engine on Debian 13

#### 1) Add Docker’s GPG key

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

#### 2) Add Docker APT repo (Trixie is Debian 13)

```bash

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### 3) Install Docker components

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

##### Validate

```bash
sudo systemctl status docker
sudo docker run hello-world
```

##### Make docker available without sudo access

```bash
sudo usermod -aG docker $USER
newgrp docker
docker ps
```

##### Validate

```bash
systemctl is-active docker
```


---

## Install Minikube

```bash
cd /tmp
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64
```

##### Check version:

`minikube version`


---

## Install kubectl

You can use upstream Kubernetes binaries so your `kubectl` matches the latest stable server version.

```bash
cd /tmp
KVER=$(curl -L -s https://dl.k8s.io/release/stable.txt)
curl -LO "https://dl.k8s.io/release/${KVER}/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```

Note: Minikube also bundles a `kubectl` that can be used as `minikube kubectl --get pods` if you prefer not to install it separately.


---

## Start Minikube on Debian (Docker driver)

##### Basic start (non‑root user):

`minikube start --driver=docker`

##### Recommended for a smoother dev experience on a typical laptop (adapt RAM/CPU):

```bash
minikube start \
  --driver=docker \
  --cpus=3 \
  --memory=8192 \
  --disk-size=30g
```

##### Check status:

```bash
minikube status
kubectl get nodes
kubectl cluster-info
```

If `minikube start` fails, common fixes:

* Ensure Docker is running: `systemctl status docker`.
* Verify you are in the `docker` group and re‑login or use `newgrp docker`.
* Add `--force-systemd=true` if cgroup driver issues appear with certain Docker setups.


---

## Quick sanity test: Hello Minikube

##### Run the classic “hello‑minikube” app:

```bash
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080
kubectl get services hello-minikube
```

Open it via Minikube’s helper:

`minikube service hello-minikube`

This should print a URL you can curl to see the echo server response.

`kubectl port-forward svc/hello-minikube --address=0.0.0.0 8080:8080`


---

## Useful addons and dashboard

##### List available addons:

`minikube addons list`

##### Typical ones to enable:

```bash
minikube addons enable dashboard
minikube addons enable ingress
minikube addons enable metrics-server
```

##### Launch dashboard:

`minikube dashboard`


---

## Daily operations on Debian

##### Common lifecycle commands:

```bash
minikube pause
minikube unpause

minikube stop

minikube delete --all

minikube config set memory 8192
minikube config set cpus 4
```

##### Multi‑node local cluster example:

```bash
minikube start --driver=docker --nodes=3 --cpus=2 --memory=4096
kubectl get nodes
```
