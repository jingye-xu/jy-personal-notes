
# 1. Check if your linux supports exFAT

Starting Linux kernel 5.4, exFAT filesystem support is enabled in the Linux kernel itself. Check which Linux kernel version you are running. If it is kernel 5.4 or higher, you should be fine (mostly).

# 2. Install packages

## Ubuntu 20.04 and lower versions:

```bash
sudo apt install exfat-fuse exfat-utils
```

## For Ubuntu 22.04 and higher:

```bash
sudo apt install exfat-fuse exfatprogs
```
