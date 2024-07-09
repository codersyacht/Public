
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

<img width="295" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/c83fa501-06e0-441d-b8de-1bf8ded7798e">
