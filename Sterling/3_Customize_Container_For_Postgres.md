## **Customizing Containers For PostgreSQL**

Refer to the following link to configure PostgreSQL for OMS.
_https://github.com/codersyacht/Public/tree/main/Postgres_

**Updating the sandbox.cfg**

```CMD
docker exec -it omruntime bash
```
```CMD
cd /opt/ssfs/runtime/properties
```
```CMD
vi sandbox.cfg
```

Add the following entry:
```PROP
POSTGRESQL=TRUE
```
Edit the following fields with the following values:
```PROP
DB_HOST=9.30.119.246
DB_PORT=5432
DB_DATA=omdb
DB_USER=omdb
DB_PASS=LabMachine4@Training
DB_SCHEMA_OWNER=omdb
JDBC_DRIVER=/opt/ssfs/runtime/jar/yfsextn/1_0/postgresql-42.2.24.jar
DB_DRIVERS=/opt/ssfs/runtime/jar/yfsextn/1_0/postgresql-42.2.24.jar
DB_VENDOR=postgresql
UI_DB_POOL=postgresqlPool
DB_POOL=postgresqlPool
```
Delete the following entry:
```PROP
DB2=TRUE
```

sandbox.cfg sample reference :
_https://github.com/codersyacht/Public/blob/main/Artifacts/postgres_sandbox.cfg_

Reference:
_https://www.ibm.com/docs/en/order-management-sw/10.0?topic=software-customizing-certified-containers_
