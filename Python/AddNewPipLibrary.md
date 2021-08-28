```
python3 -m pip config set install.trusted-host {ip address}
python3 -m pip config set global.extra-index-url http://{ip address:port}/repository/python/simple
python3 -m pip config set global.timeout 1
python3 -m pip config set global.retries 1
```
