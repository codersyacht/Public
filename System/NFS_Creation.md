# **NFS Creation**

**Install NFS**

sudo su

```CMD
sudo yum install nfs-utils -y
```
```CMD
systemctl start nfs-server.service
```
```CMD
systemctl enable nfs-server.service
```
**Firewall Configuration**

**Option 1:**

If the environment is non production and if security is not a constraint, firewall can be disabled.

```CMD
systemctl stop firewalld
```
```CMD
systemctl disable firewalld
```
To start the firewall.

```CMD
systemctl enable firewalld
```
```CMD
systemctl start firewalld
```
**Option 2:**

If firewall cannot be disabled.

```CMD
firewall-cmd --permanent --add-service=nfs
```
```CMD
firewall-cmd --permanent --add-service=rpc-bind
```
```CMD
firewall-cmd --permanent --add-service=mountd
```
```CMD
firewall-cmd --reload
```
```CMD
firewall-cmd --list-all
```

**Configure NFS Folder**

Assume pwd is /home/admin/.

```CMD
mkdir omshare
```
```CMD
chown admin:admin ./omshare
```
```CMD
chmod 777 ./omshare
```
```CMD
vi /etc/exports
```
```TEXT
/home/admin/omshare *(rw,sync)
```
```CMD
exportfs -avr
```
```CMD
exportfs  -s
```
```CMD
exit
```

**Mounting a folder**
```CMD
mkdir -p ./mnt/omshare
```
```CMD
sudo su
```
```CMD
mount -t nfs 127.0.0.1:/home/admin/omshare /home/admin/mnt/omshare
```
```CMD
exit
```
Test by placing a file under /home/admin/mnt/omshare. Check if it is seen under /home/admin/omshare

**Unmounting**
```CMD
umount /home/admin/apps/mnt/omshare
```
Test by placing a file under /home/admin/mnt/test and see if the file is visible in /home/admin/omshare

