**Uninstall PostgreSQL**

```CMD
sudo su -
```

```CMD
yum remove yum remove postgresql-server
```

Check and delete /var/lib/pgsql
Check of all postgres files in /user/bin are deleted

ls -lrt /user/bin | grep postgres

delete /home/postgres/data
