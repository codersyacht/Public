# **Minikube**

**Prerequisite:** <br>
Docker Installation.<br>
https://github.com/codersyacht/public/blob/main/system/Docker_Installation_General.md

KVM Hypervisor Installation:<br>
https://github.com/codersyacht/public/blob/main/system/KVM_Hypervisor_Installation.md

### Minikube Installation

Update yum package:
```CMD
sudo yum update -y
```

Download the minikube package
```CMD
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

Install the minikube software
```CMD
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Start Minikube
```CMD
minikube start --memory 24576 --cpus 8
```

😄  minikube v1.32.0 on Centos 9 (kvm/amd64) <br>
✨  Automatically selected the docker driver <br>
📌  Using Docker driver with root privileges <br>
👍  Starting control plane node minikube in cluster minikube <br>
🚜  Pulling base image ... <br>
🔥  Creating docker container (CPUs=2, Memory=8192MB) ... <br>
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ... <br>
    ▪ Generating certificates and keys ... <br>
    ▪ Booting up control plane ... <br>
    ▪ Configuring RBAC rules ... <br>
🔗  Configuring bridge CNI (Container Networking Interface) ... <br>
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5 <br>
🔎  Verifying Kubernetes components... <br>
🌟  Enabled addons: storage-provisioner, default-storageclass <br>
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default <br>


Check Minikube version
```CMD
minikube version
```
Check the return value, example: 
minikube version: v1.32.0 <br>
commit: 8220a6eb95f0a4d75f7f2d7b14cef975f050512d

Set kubctl alias
```CMD
alias kubectl="minikube kubectl --"
```
```CMD
sudo ln -s $(which minikube) /usr/local/bin/kubectl
```
Check Kubectl version:
```CMD
kubectl version --client -o json
```
Check the output, example:
```JSON
{
  "clientVersion": {
    "major": "1",
    "minor": "28",
    "gitVersion": "v1.28.3",
    "gitCommit": "a8a1abc25cad87333840cd7d54be2efaf31a3177",
    "gitTreeState": "clean",
    "buildDate": "2023-10-18T11:42:52Z",
    "goVersion": "go1.20.10",
    "compiler": "gc",
    "platform": "linux/amd64"
  },
  "kustomizeVersion": "v5.0.4-0.20230601165947-6ce0bf390ce3"
}
```
**Start and Stop Minikube**
Stop minikube:
```CMD
minikube stop
```
Restart minikube:
```CMD
minikube start --memory 24576 --cpus 8
```

😄  minikube v1.32.0 on Centos 9 (kvm/amd64) <br>
✨  Using the docker driver based on existing profile <br>
👍  Starting control plane node minikube in cluster minikube <br>
🚜  Pulling base image ... <br>
🔄  Restarting existing docker container for "minikube" ... <br>
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ... <br>
🔗  Configuring bridge CNI (Container Networking Interface) ... <br>
🔎  Verifying Kubernetes components... <br>
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5 <br>
🌟  Enabled addons: storage-provisioner, default-storageclass <br>
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default <br>

Delete minikube:
Stop minikube and execute:
```CMD
minikube delete
```
🔥  Deleting "minikube" in docker ...
🔥  Deleting container "minikube" ...
🔥  Removing /home/admin/.minikube/machines/minikube ...
💀  Removed all traces of the "minikube" cluster.

### Enable Ingress Controller

```CMD
minikube addons enable ingress
```
```CMD
kubectl get services -n ingress-nginx
```

