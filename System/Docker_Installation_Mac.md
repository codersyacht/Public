
# **Docker Installation**

**Prerequisite** <br>
Ensure you are installating as a non root user with sudo access.<br>
Install Homebrew<br>
Reference:<br> 
https://github.com/codersyacht/Public/blob/main/System/Homebrew%20Internals.md

**Install Docker**
```CMD
brew install docker
```
****Install Docker-compose**
```CMD
brew install docker-compose**
```
**Install Colima**
```CMD
brew install colima
```

**Start colima**
```CMD
colima start --cpu 8 --memory 16 --disk 100
```

**Check docker**
```CMD
docker ps
```
**Troubleshooting**

If the following error is observer. <br><br>
Error saving credentials: error storing credentials - err: exec: "docker-credential-desktop": executable file not found in $PATH, out: `` <br>
do the following:
```CMD
sudo vi ~/.docker/config.json
```
Rename credsStore to credStore and save.
