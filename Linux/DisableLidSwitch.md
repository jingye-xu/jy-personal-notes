# How to disable auto suspend when you close laptop lid

1. Edit `/etc/systemd/logind.conf` and make sure you have:
    ```
    HandleLidSwitch=ignore
    ```
2. Make changes go into effect
    ```
    systemctl restart systemd-logind
    ```
    
