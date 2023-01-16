# plex linuxserver/plex

Easiest way to deploy using docker
```
docker run -d \
  --name=plex \
  --net=host \
  -e PUID=* \
  -e PGID=* \
  -e VERSION=docker \
  -e PLEX_CLAIM=*** \
  --device /dev/dri:/dev/dri \
  -v /src/plex/config:/config \
  -v /media:/data \
  --restart always \
  lscr.io/linuxserver/plex:latest
```

## Parameters

### -e PUID= and -e PGID=

use `id username` to check to uid and gid

```
root@pve:~# id root
uid=0(root) gid=0(root) groups=0(root)
```

### -e PLEX_CLAIM

Obtain a claim token from https://plex.tv/claim and input here. Keep in mind that the claim tokens expire within 4 minutes.
