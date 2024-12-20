# **Docker Installation**

**Prerequisite:** <br>
User Account Creation. <br>
https://github.com/codersyacht/public/blob/main/system/Linux_User_Creation.md

**1. Install yum utis.**

Run the following command for sudo rights.

```CMD
sudo su
```
Provide the password.

Execute the following command:

```CMD
sudo yum install -y yum-utils
```

**2. Installing Docker**

Execute the following command to add the docker repository:

```CMD
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
Install Docker using the following command:

```CMD
sudo yum install -y docker-ce docker-ce-cli containerd.io
```

Run the following command to install Docker compose.

```CMD
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```CMD
sudo chmod +x /usr/local/bin/docker-compose
```

Exit sudo user using exit command.

```CMD
exit
```

**3. Manage Docker as non-root user**

Create a Unix group called docker and add users to it.

Create a new group _docker_.
```CMD
sudo groupadd -f docker
```
Add user _admin_ to _docker_ group.
```CMD
sudo usermod -aG docker $USER
```
Run the following command to activate the changes to groups:
```CMD
newgrp docker
```

Run groups command to verify.
```CMD
groups
```

**4. Start Docker**

Execute the following commands to start docker service:
```CMD
sudo systemctl start docker
```
Test the installation by executing the following commands:
To check for the list of images available in the local repository:
```CMD
docker images
```
To check if there are any active container:
```CMD
docker ps
```
To check if there are any exited containers:
```CMD
docker ps -a
```
For now both the above commands would return no values.

