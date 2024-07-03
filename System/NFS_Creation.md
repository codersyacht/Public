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
systemctl start firewalld

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

```CMD
mkdir omshare
```
```CMD
chown admin:admin ./omshare
```CMD
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
mkdir -p ./mnt/omshare

sudo su

mount -t nfs 127.0.0.1:/home/admin/omshare /home/admin/apps/mnt/omshare

exit

 umount /home/admin/apps/mnt/omshare

Test by placing a file under /home/admin/mnt/test and see if the file is visible in /home/admin/omshare

