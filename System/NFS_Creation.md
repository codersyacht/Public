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
```CMD
systemctl start nfs-server.service
```
```CMD
systemctl enable nfs-server.service
```
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

mkdir omshare

chown admin:admin /omshare

chmod 777 /omshare


vi /etc/exports

/home/admin/omshare *(rw,sync)

exportfs -avr
exportfs  -s

exit

mkdir -p ./mnt/omshare

sudo su

mount -t nfs 127.0.0.1:/home/admin/omshare /home/admin/apps/mnt/omshare

exit

 umount /home/admin/apps/mnt/omshare

Test by placing a file under /home/admin/mnt/test and see if the file is visible in /home/admin/omshare

