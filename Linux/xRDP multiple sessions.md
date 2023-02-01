# xRDP multiple sessions

## 1. Open startwm.sh

```bash
sudo nano /etc/xrdp/startwm.sh
```

## 2. Locate the line test -x /etc/X11/Xsession && exec /etc/X11/Xsession and just above it add the following command

```bash
export $(dbus-launch)
```

## 3. Save the file
