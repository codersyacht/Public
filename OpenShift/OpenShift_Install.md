## Installing OpenShift Local

### 1. Create a non-root user account in linux.

Follow the instruction in the link below:

https://github.com/codersyacht/Tutorials/blob/main/System/Linux_User_Creation.md

### 2. Update yum

```CMD
yum update -y
```

### 3. Logging into Red Hat website to download the installables.
   
Login or if not registered register in the following Red Hat website.

_https://console.redhat.com/_
   
Click "_Red Hat OpenShift_". 
Click on "_Create Cluster_".

<img width="1002" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/956f7570-5ee3-4454-8cff-1ecbf67332e6">


_figure 1: Red Hat console home page._

Under "_Select an OpenShift cluster type to create_" select "_Local_".

<img width="1002" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/6ebcde7e-ee4b-4a2b-b673-2fd31b2fcca8">


_figure 2: Choosing cluster type._

Choose Linux or the right operating system and click on "_Download OpenShift Local_".

Get the secret by clicking the "_Download Pull secret_".

This would have downloaded 2 files into your local system namely crc-linux-amd64.tar.xz and pull-secret.txt.

Move the downloaded files to the linux server under the non-root (admin) user. I have moved the files into /home/admin/apps/ocp.

### 4. Installing Code Ready Container.

Extract the tar file.
```CMD
tar -xvf crc-linux-amd64.tar.xz
```
Rename the extracted folder to openshiftlocal.
```CMD
mv crc-linux-2.36.0-amd64 openshiftlocal
```
Navigate to user home durectory. 
```CMD
cd /home/admin
```
Create a bin directory.
```CMD
mkdir ~/bin
```
Navigate to apps/ocp directory and execute the following command.
```CMD
cp openshiftlocal/crc ~/bin
```
Export bin folder path.
```CMD
export PATH=$PATH:$HOME/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
```
Run crc setup.
```CMD
crc setup
```

On successful installation the following message will be displayed.
```
Your system is correctly setup for using CRC. Use 'crc start' to start the instance.
```

### 5. Configuring Code Ready Container.

Execute the following command.
```CMD
crc config set cpus 8
crc config set memory 24576
crc config set disk-size 200
crc config set enable-cluster-monitoring true
crc config set pull-secret-file /home/admin/apps/ocp/pull-secret.txt
crc config set consent-telemetry no
crc config set skip-check-daemon-systemd-sockets true     # Only if it's required.
crc config set skip-check-daemon-systemd-unit true        # Only if it's required.
```

### 6. Start Code Ready Container.

Run the following command.
```CMD
crc start
```
While staring please note the following messages.
```
INFO Starting CRC VM for openshift 4.15.12...     
INFO CRC instance is running with IP 192.168.130.11
```
The above means the cluster is accessible on local ip address 192.168.130.11.
On successul start of code ready container, the following message will be displayed.

```
Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: iViGY-aRiLA-hV5t8-XK4iM

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u developer https://api.crc.testing:6443
```

  Refer to /etc/hosts file. Note the following entties.
  
#Added by CRC
192.168.130.11   api.crc.testing canary-openshift-ingress-canary.apps-crc.testing console-openshift-console.apps-crc.testing default-route-openshift-image-registry.apps-crc.testing downloads-openshift-console.apps-crc.testing oauth-openshift.apps-crc.testing

The above is within the linuc machine. If you want to access the OpenShift console from a remote machine, the following entries has to be manually made in the remote machine's /etc/hosts file as shown below. Here, the IP 9.30.188.230 is the actual IP of the linux machine.

9.30.188.230 api.crc.testing canary-openshift-ingress-canary.apps-crc.testing console-openshift-console.apps-crc.testing default-route-openshift-image-registry.apps-crc.testing downloads-openshift-console.apps-crc.testing oauth-openshift.apps-crc.testing

### 7. Checking status of Code Ready Container.

```CMD
crc status
```
<img width="1002" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/36e8406b-aa23-4ecb-ba87-6824525bba13">



_figure 3: crc status output_

### 8. Console url.

```CMD
crc console --url
```
### 9. To access oc command.

To access oc command for OpenShift command execution run the following command.
```CMD
eval $(crc oc-env)cd /usr/bin/
```
### 10. Check if pods are running
```CMD
oc get pod --all-namespaces
```
<img width="1002" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/02c566f5-c2b1-449c-a739-846e2be40d5f">



figure 4: get pods output.

### 11. Exposing port 444 and 80.

Execute the following command.
```CMD
sudo su
sysctl net.ipv4.ip_unprivileged_port_start=80
sysctl net.ipv4.ip_unprivileged_port_start=443
exit
```
```CMD
oc port-forward --address 0.0.0.0 svc/router-internal-default -n openshift-ingress 443:443
```

Following message is displayed in routing is successful.
Forwarding from 0.0.0.0:443 -> 443

### OpenShift Console.

Access the Openshift hopepage using the following link.

https://console-openshift-console.apps-crc.testing/

uername is kubeadmin. Password is **iViGY-aRiLA-hV5t8-XK4iM** (Received at time of crc start).

<img width="1002" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/035f75d3-1cf8-43cd-8c1b-aec590634c0d">



_figure 5: OpenShift console home page._

