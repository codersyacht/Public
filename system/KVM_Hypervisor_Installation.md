
### KVM Hypervisor Installation

```CMD
sudo yum update -y
```
```CMD
sudo yum install -y qemu-kvm qemu-img libvirt virt-install libvirt-client
```
```CMD
sudo systemctl enable --now libvirtd
```
```CMD
sudo systemctl status libvirtd
```
```Output
[admin@sipserver1 ~]$ sudo systemctl status libvirtd
● libvirtd.service - libvirt legacy monolithic daemon
     Loaded: loaded (/usr/lib/systemd/system/libvirtd.service; enabled; preset: disabled)
     Active: active (running) since Wed 2024-10-30 03:03:11 PDT; 18s ago
TriggeredBy: ● libvirtd-admin.socket
             ● libvirtd-ro.socket
             ● libvirtd.socket
       Docs: man:libvirtd(8)
             https://libvirt.org/
   Main PID: 94167 (libvirtd)
      Tasks: 22 (limit: 32768)
     Memory: 19.5M
        CPU: 454ms
     CGroup: /system.slice/libvirtd.service
             ├─94167 /usr/sbin/libvirtd --timeout 120
             ├─94269 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper
             └─94270 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper

Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq-dhcp[94269]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq-dhcp[94269]: DHCP, sockets bound exclusively to interface virbr0
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: reading /etc/resolv.conf
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: using nameserver 9.30.99.253#53
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: using nameserver 9.30.6.100#53
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: using nameserver 10.11.64.21#53
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: using nameserver 10.11.64.22#53
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: read /etc/hosts - 3 addresses
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq[94269]: read /var/lib/libvirt/dnsmasq/default.addnhosts - 0 addresses
Oct 30 03:03:12 sipserver1.fyre.ibm.com dnsmasq-dhcp[94269]: read /var/lib/libvirt/dnsmasq/default.hostsfile
```

```CMD
sudo usermod -a -G libvirt $(whoami)
```
```CMD
newgrp libvirt
```
```CMD
sudo vi /etc/libvirt/libvirtd.conf
```
```CMD
unix_sock_group = "libvirt"
unix_sock_rw_perms = "0770"
```
```CMD
sudo systemctl restart libvirtd
```
