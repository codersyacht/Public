## **Install 3rd Party Jars**

**Install 3rd Party Jars**
```CMD
./install3rdParty.sh yfsextn 1_0 -j /root/apps/dtk/3rdpartyjars/* -targetJVM EVERY
```

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
```
```CMD
rm 3rdpartyjars.tar
```
```CMD
chmod 777 -R 3rdpartyjars/
```

```CMD
cd /opt/ssfs/runtime/bin/
```
```CMD
./install3rdParty.sh yfsextn 1_0 -j /opt/ssfs/3rdpartyjars/* -targetJVM EVERY
```

Verify if the jars are installed successfully.

<img width="790" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/58b893ef-3d3d-4f29-9c06-d72ba2269231">


Check the entries in the AGENTDynamicclasspath.cfg, APPDynamicclasspath.cfg and dynamicclasspath.cfg to ensure the jar reference are added.
