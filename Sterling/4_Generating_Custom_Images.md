## **Generating Custom Images**

```CMD
docker exec -it omruntime bash
```

Navigate to /opt/ssfs/runtime/container-scripts/imagebuild/

```CMD
./generateImages.sh --DEV_MODE=true
```
If the images are successfully generated, the following images will be listed.

<img width="855" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/dc362bc0-ab34-411b-8f0a-c8e7288c755a">

**Tagging images**
```CMD
buildah tag 0a8ec8678410  docker.io/codersyacht/om-app:V10.02
```
```CMD
buildah tag a772e4ec0b5a docker.io/codersyacht/om-agent:V10.02
```

**Logging into Docker hub using buildah**

<img width="650" alt="image" src="https://github.com/codersyacht/Public/assets/128015499/9b7ce34e-982b-4e6e-a1af-5df12ff5ac12">



**Pushing the images to docker hub**
```CMD
buildah push docker.io/codersyacht/om-agent:V10.02
```
```CMD
buildah push docker.io/codersyacht/om-app:V10.02
```
Ensure the images are successfully uploaded. Log into docker hub to confirm the same.





