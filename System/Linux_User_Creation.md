### User Setup

**1. Create user admin.**

```CMD
useradd admin
```
```CMD
passwd admin
```

**2. Provide root access to admin user.**

Type visudo and edit the file by adding the following line under "_Allow root to run any commands anywhere_".

```script
admin    ALL=(ALL)   ALL
```
<img width="524" alt="image" src="https://github.com/codersyacht/Tutorials/assets/128015499/e41b0399-ffd5-470b-9a29-3069ecbe48d8">

**3. Add the user to wheel group.**

The wheel group is a special user group used to control access to the su or sudo command, which allows a user to masquerade as another user (usually the super user).

```CMD
sudo usermod -aG wheel admin
```
Exit and login back as admin user.

**Delete user from a group.**

```script
gpasswd -d <user> <group>
```

**4. Check a user in a group.**

```script
groups <user>
```

**5. Check all users in a group.**

```script
getent group <group>
```
