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
mkdir omshare

chown admin:root /omshare

chmod 777 /omshare

vi /etc/exports

![image](https://github.com/codersyacht/Tutorials/assets/128015499/96194cf7-9247-4e0a-b94d-75643069a6d2)

![image](https://github.com/codersyacht/Tutorials/assets/128015499/7acbeae2-a66c-4054-9b31-b23c970a5288)


mkdir omshare

chmod 777 omshare
chmod admin:admin omshare

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

