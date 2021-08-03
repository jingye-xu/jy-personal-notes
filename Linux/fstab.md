File path:
    ```
    /etc/fstab
    ```
# An example of an fstab file:
```
# device-spec   mount-point   fs-type  options  dump pass
```
The space or tab-separated fields within each row must appear in a specific order:

1. device-spec – The device name, label, UUID, or other means of specifying the partition or data source this entry refers to.
2. mount-point – Where the contents of the device may be accessed after mounting; for swap partitions or files, this is set to none.
3. fs-type – The type of file system to be mounted.
4. options – Options describing various other aspects of the file system, such as whether it is automatically mounted at boot, which users may mount or access it, whether it may be written to or only read from, its size, and so forth; the special option defaults refers to a pre-determined set of options depending on the file system type.
5. dump – A number indicating whether and how often the file system should be backed up by the dump program; a zero indicates the file system will never be automatically backed up.
6. pass – A number indicating the order in which the fsck program will check the devices for errors at boot time:
    ```
    0 - do not check
    1 - check immediately during boot
    2 - check after boot
    ```
# Tips
1. The `nofail` option helps make sure that the VM starts even if the file system is corrupted or the file system doesn't exist at startup. We recommend that you use the nofail option in the fstab file to enable startup to continue after errors occur in partitions that are not required for the VM to start.
    ```
    UUID=4706-0137  /media/sda1     ntfs    defaults,nofail  0 0
    ```
2. Use the following command to check if the fatab file correctly modified:
    ```
    sudo mount -a
    ```
