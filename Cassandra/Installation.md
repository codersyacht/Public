### **Cassandra Installation**

Login as Cassandra user.

```CMD
sudo su
```

```CMD
yum update -y
```

If Java is not installed, install Java.

```CMD
yum install java -y
```

Create a file /etc/yum.repos.d/cassandra.repo with the following content.
[cassandra]
name=Apache Cassandra
baseurl=https://redhat.cassandra.apache.org/41x/
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://downloads.apache.org/cassandra/KEYS
Update the yum repository.
yum update -y
