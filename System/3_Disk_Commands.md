## **Disk Commands**

**Check Disk Space**

```CMD
df -h
```

***Retrieve Top Largest files***
```CMD
sudo du -a /home | sort -n -r | head -n 10
```

***Retrieve Folders Size Including Sub Folders and Files.

```CMD
du -sh *
```
To include hidden files:
```CMD
du -hs .[^.]*
```
