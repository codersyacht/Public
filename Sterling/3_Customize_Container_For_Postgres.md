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

If you are using the reference file, copy the sandbox.cfg into the container.
```CMD
docker cp sandbox.cfg omruntime:/opt/ssfs/runtime/properties/
```
From the runtime's bin directory, execute the following commands.

```CMD
./setupfiles.sh
```
```
```
./dbverify.sh
```

Ensure no error is thrown.

<img width="855" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/56b22770-707c-4b91-9183-b9e008308b9c">

Reference:

_https://www.ibm.com/docs/en/order-management-sw/10.0?topic=software-customizing-certified-containers_
