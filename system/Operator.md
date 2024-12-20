# **Operator Installation**

Prerequisite:<br>
Minikube Installation. <br> 
https://github.com/codersyacht/public/blob/main/System/Minikube_Installation.md

**Set platform Information**
```CMD
export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
```
```CMD
export OS=$(uname | awk '{print tolower($0)}')
```

**Download the binary for your platform**
```CMD
export OPERATOR_SDK_DL_URL=https://github.com/operator-framework/operator-sdk/releases/download/v1.38.0
```
```CMD
curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}
```

**Verify the downloaded binary**
Import the operator-sdk release GPG key from keyserver.ubuntu.com:
```CMD
gpg --keyserver keyserver.ubuntu.com --recv-keys 052996E2A20B5C7E
```

Download the checksums file and its signature, then verify the signature:
```CMD
curl -LO ${OPERATOR_SDK_DL_URL}/checksums.txt
```
```CMD
curl -LO ${OPERATOR_SDK_DL_URL}/checksums.txt.asc
```
```CMD
gpg -u "Operator SDK (release) <cncf-operator-sdk@cncf.io>" --verify checksums.txt.asc
```
```
[admin@sipserver1 ~]$ gpg -u "Operator SDK (release) <cncf-operator-sdk@cncf.io>" --verify checksums.txt.asc
gpg: assuming signed data in 'checksums.txt'
gpg: Signature made Thu 05 Oct 2023 01:06:56 PM PDT
gpg:                using RSA key 8613DB87A5BA825EF3FD0EBE2A859D08BF9886DB
gpg: Good signature from "Operator SDK (release) <cncf-operator-sdk@cncf.io>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 3B2F 1481 D146 2380 80B3  46BB 0529 96E2 A20B 5C7E
     Subkey fingerprint: 8613 DB87 A5BA 825E F3FD  0EBE 2A85 9D08 BF98 86DB
```

Check if the checksum matches
```CMD
grep operator-sdk_${OS}_${ARCH} checksums.txt | sha256sum -c -
```
Expected output:
operator-sdk_linux_amd64: OK

**Install Operator**
```CMD
chmod +x operator-sdk_${OS}_${ARCH} && sudo mv operator-sdk_${OS}_${ARCH} /usr/local/bin/operator-sdk
```

**Check Operator SDK version**
```CMD
operator-sdk version
```
Output:
operator-sdk version: "v1.32.0", commit: "4dcbbe343b29d325fd8a14cc60366335298b40a3", kubernetes version: "1.26.0", go version: "go1.19.13", GOOS: "linux", GOARCH: "amd64"

**Install Operator OLM**

Command to installation Operator Lifesycvle Manager
```CMD
operator-sdk olm install
```
Result should show:
INFO[0014] Successfully installed OLM version "latest" 

Execute the following command:
```CMD
kubectl get pods --all-namespaces
```
The result should show the following result:

```
NAMESPACE     NAME                               READY   STATUS    RESTARTS        AGE
kube-system   coredns-6f6b679f8f-mdj55           1/1     Running   0               5m9s
kube-system   etcd-minikube                      1/1     Running   0               5m14s
kube-system   kube-apiserver-minikube            1/1     Running   0               5m14s
kube-system   kube-controller-manager-minikube   1/1     Running   0               5m14s
kube-system   kube-proxy-nxd6c                   1/1     Running   0               5m9s
kube-system   kube-scheduler-minikube            1/1     Running   0               5m14s
kube-system   storage-provisioner                1/1     Running   1 (4m38s ago)   5m12s
olm           catalog-operator-9f6dc8c87-jgl29   1/1     Running   0               85s
olm           olm-operator-6bccddc987-mmlzf      1/1     Running   0               85s
olm           operatorhubio-catalog-4nb9d        1/1     Running   0               73s
olm           packageserver-956c95f97-kwpgv      1/1     Running   0               73s
olm           packageserver-956c95f97-tpl5z      1/1     Running   0               73s
```
