**Start database**
```CMD
postgres -D /home/postgres/data >/home/postgres/dbstart.log 2>&1 &
```

**Create DB**

```CMD
createdb omdb
```

**Create User with password and create schema**

```CMD
psql -h localhost -p 5432 -U postgres omdb
```
```CMD
CREATE USER omdb WITH PASSWORD 'LabMachine4@Training';
or
ALTER USER omdb WITH PASSWORD 'LabMachine4@Training';
``
```CMD
CREATE SCHEMA IF NOT EXISTS omdb AUTHORIZATION omdb;
```
```CMD
\q
```
**Restart database**

Kill the running process id and execute the following command.

```CMD
postgres -D /home/postgres/data >/home/postgres/dbstart.log 2>&1 &
```

**Delete Database**

```CMD
dropdb OMDB
```

**Accessing Postgresql port from remote machine**

If there is any issue will accessing port 5432 from outside the machine, try after disabling the firewall.
```CMD
sudo systemctl status firewalld
```
```CMD
sudo systemctl stop firewalld
```

