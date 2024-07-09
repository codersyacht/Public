**Creating a new user postgresql**

```CMD
useradd postgres
```

**Setting password for user postgres**

```CMD
passwd postgres
```

**Provide root access to postgres user**

Type the following command:
```CMD
visudo
```
Add the following line:


postgres    ALL=(ALL)   ALL

<img width="367" alt="image" src="https://github.com/codersyacht/Tutorials/assets/128015499/b2d5d185-35c3-4182-994d-10e4b65d8a4b">


Run the following command:

```CMD
sudo usermod -aG wheel postgres
```
exit and login back as postgres.


**Installation of PostgreSQL**

```CMD
su -
```
```CMD
yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
```
```CMD
yum --disablerepo=* -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-9-x86_64/pgdg-redhat-repo-latest.noarch.rpm
```

```CMD
yum update -y
```
```CMD
yum install -y postgresql14-server
```
```CMD
exit
```
```CMD
export PATH=/usr/pgsql-14/bin:$PATH
```

**Initialize Postgres database system**

```CMD
su - postgres
```
```CMD
export PATH=/usr/pgsql-14/bin:$PATH
```
```CMD
initdb -D /home/postgres/data -U postgres
```
```CMD
exit
```
**Modify Configuration**

```CMD
echo "listen_addresses='*'" >> /home/postgres/data/postgresql.conf
echo 'host            all     all             0.0.0.0/0                     password' >> /home/postgres/data/pg_hba.conf
```

**Start database**
```CMD
postgres -D /home/postgres/data >/home/postgres/dbstart.log 2>&1 &
```
