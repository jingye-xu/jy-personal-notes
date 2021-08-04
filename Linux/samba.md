# 1. Configure samba server
## 1. Install samba server
```
# apt install samba
```

## 2. Verfy the server installation
```
root@pve:~# systemctl status nmbd
● nmbd.service - Samba NMB Daemon
     Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: enabl>
     Active: active (running) since Tue 2021-08-03 20:39:01 CDT; 41s ago
       Docs: man:nmbd(8)
             man:samba(7)
             man:smb.conf(5)
   Main PID: 236538 (nmbd)
     Status: "nmbd: ready to serve connections..."
      Tasks: 1 (limit: 14190)
     Memory: 3.3M
        CPU: 39ms
     CGroup: /system.slice/nmbd.service
             └─236538 /usr/sbin/nmbd --foreground --no-process-group

Aug 03 20:39:01 pve systemd[1]: Starting Samba NMB Daemon...
Aug 03 20:39:01 pve systemd[1]: Started Samba NMB Daemon.
```

## 3. Configure samba server
Goals:  
    1. Samba server cannot allow guest access.  
    2. Create a folder named "haredFolder".  
    3. Users under group "smbedit" have whole control on the folder.  
    4. Users under group "smbview" can only read the contents.  

### 1. Create a folder and set the permission  
```
# mkdir /media/sharedFolder
# chmod 777 sharedFolder/
```

### 2. Create group and users
```
# groupadd smbedit
# groupadd smbview
# useradd edit01 -g smbedit
# useradd view01 -g smbview
```

### 3. Set samba password
```
root@pve:/media# smbpasswd -a edit01
New SMB password:
Retype new SMB password:
Added user edit01.
root@pve:/media# smbpasswd -a view01
New SMB password:
Retype new SMB password:
Added user view01.
```

### 4. Configure `/etc/samba/smb.conf`
1. Backup the original file  
```
# mv smb.conf smb.conf.bk
```
2. Create a new smb.conf file  
```
# nano smb.conf
```
3. the whole contents inside the file:  
```
root@pve:/etc/samba# cat smb.conf
[global]
workgroup = WORKGROUP
server string = Samba File Server
security = user
encrypt passwords = yes

[sharedFolder]
comment = shared folder
path = /media/sharedFolder
public = no
valid users = @smbedit,@smbview
write list = @smbedit
printable = no
```

### 5. Restart samba server
```
# systemctl restart nmbd.service
```

# 2. Configure samba client (Linux)