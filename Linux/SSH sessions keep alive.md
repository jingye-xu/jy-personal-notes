# SSH sessions keep alive

* To enable the keep alive system-wide (root access required), edit `/etc/ssh/ssh_config`;
* To set the settings for just your user, edit `~/.ssh/config` (create the file if it doesn’t exist). Insert the following:
```
Host *
    ServerAliveInterval 300
    ServerAliveCountMax 2
```
**Note**: Host * means any hosts that connect to this server. 
