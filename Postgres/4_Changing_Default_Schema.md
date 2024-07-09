
```CMD
psql -h localhost -p 5432 -U postgres
```

```SQL
ALTER DATABASE omdb SET search_path TO omdb;
```
```CMD
psql -h localhost -p 5432 -U postgres omdb
```
```SQL
SHOW SEARCH_PATH;
```

 search_path 
-------------
 "OMDB"
(1 row)
