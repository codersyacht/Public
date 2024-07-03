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
**Firewall Configuration **

systemctl start nfs-server.service

systemctl enable nfs-server.service

firewall-cmd --permanent --add-service=nfs

firewall-cmd --permanent --add-service=rpc-bind

firewall-cmd --permanent --add-service=mountd

firewall-cmd --reload

firewall-cmd --list-all


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

