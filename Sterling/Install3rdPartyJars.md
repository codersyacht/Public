## **Install 3rd Party Jars**

**Installing 3rd Party Jars in a runtime container for customization**

Copy the custom jar present in the base operating system into the runtime container.

Assume the jars are present in the following directory of the base OS.
/home/admin/apps/omruntime/3rdpartyjars

Run the following commnand from /home/admin/apps/omruntime :
```CMD
tar -cvf 3rdpartyjars.tar ./3rdpartyjars/
```
```CMD
docker cp 3rdpartyjars.tar omruntime:/opt/ssfs
```

```CMD
docker exec -it omruntime bash
```
```
cd /opt/ssfs
```
```CMD
tar -xvf 3rdpartyjars.tar
rm 3rdpartyjars.tar
```

```CMD
cd /opt/ssfs/runtime/bin/

```CMD
./install3rdParty.sh yfsextn 1_0 -j /root/apps/dtk/3rdpartyjars/* -targetJVM EVERY
```
