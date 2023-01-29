# Jellyfin general command
```
docker run -d \
--name jellyfin \
-v /src/jellyfin/config:/config \
-v /src/jellyfin/cache:/cache \
-v /media/sharedFolder:/media \
--net=host \
--restart always \
jellyfin/jellyfin:latest
```
Where:
`/src/jellyfin/config` stores the contents in `/config` of the docker  
`/src/jellyfin/cache` stores the contents in `/cache` of docker  
`/media` stores the contents in `/media` of docker  

## If you want to add hardware acceleration device
In order to use hardware acceleration in Docker, the devices must be passed to the container. To see what video devices are available, you can run sudo lshw -c video or vainfo on your machine. VAAPI may require the render group added to the docker permissions. The render group id can be discovered in /etc/group such as `render:x:122`: 
Here we got the render group id is 103, so add follows:
```
--device /dev/dri/renderD128:/dev/dri/renderD128 --device /dev/dri/card0:/dev/dri/card0 --group-add=103
```
Make sure the path is right.

## 8096 is the default port

## use `id {username}` to check PUID and PGID

## Qnap NAS

```
docker run -d \
--name jellyfin \
-v /share/CACHEDEV1_DATA/Container/dockers/jellyfin/config:/config \
-v /share/CACHEDEV1_DATA/Container/dockers/jellyfin/cache:/cache \
-v /share/CACHEDEV2_DATA/medias:/media \
-e PUID=1000 \
-e PGID=100 \
-e TZ=America/Chicago \
--net=host \
--restart always \
--device /dev/dri:/dev/dri \
jellyfin/jellyfin:latest
```

## Other alternative jellyfin

* lscr.io/linuxserver/jellyfin:latest
* nyanmisaka/jellyfin
