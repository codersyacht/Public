
# **Docker Installation**

**Prerequisite** <br>
Ensure you are installating as a non root user with sudo access.<br>
Install Homebrew<br>
Reference:<br> 
_https://github.com/codersyacht/public/blob/main/system/Homebrew.md_

**Install Docker**
```CMD
brew install docker
```
**Install Docker-compose**
```CMD
brew install docker-compose
```
**Install Colima**
```CMD
brew install colima
```

**Start colima**
```CMD
colima start --cpu 8 --memory 16 --disk 100
```

***Check docker**
```CMD
docker ps
```
