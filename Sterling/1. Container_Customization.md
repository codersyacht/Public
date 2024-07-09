**Customizing Certified Containers**

```CMD
export ENTITLED_REGISTRY=cp.icr.io 
```
```CMD
export ENTITLED_REGISTRY_USER=cp
```
```CMD
export ENTITLED_REGISTRY_KEY="$(<ibm-entitlement-key)"
```
```CMD
docker login -u $ENTITLED_REGISTRY_USER -p $ENTITLED_REGISTRY_KEY $ENTITLED_REGISTRY
```

```CMD
docker pull cp.icr.io/cp/ibm-oms-enterprise/om-base:10.0.2406.0-amd64
```
<img width="803" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/89fde1cb-1855-4381-9a56-4d2b63287e8f">


```CMD
docker volume create omruntime
```
```CMD
docker run -e LICENSE=accept -e LANG --privileged -v omruntime:/images  -idt --name omruntime <image>
```
```CMD
docker exec -it omruntime bash
```
```CMD
./generateImages.sh --DEV_MODE=true
```

