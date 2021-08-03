# Display configurations
## Show physical volumes
```
root@pve:~# pvs
  PV         VG  Fmt  Attr PSize    PFree  
  /dev/sda3  pve lvm2 a--  <476.44g <16.00g
```

## Show volume groups
```
root@pve:~# vgs
  VG  #PV #LV #SN Attr   VSize    VFree  
  pve   1   5   0 wz--n- <476.44g <16.00g
```

## Show logical volumes
```
root@pve:~# lvs
  LV            VG  Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  data          pve twi-aotz-- <349.31g             2.30   0.59                            
  root          pve -wi-ao----   96.00g                                                    
  sharedFolder  pve Vwi-a-tz--   80.00g data        0.63                                   
  swap          pve -wi-ao----    8.00g                                                    
  vm-100-disk-0 pve Vwi-aotz--   20.00g data        37.62 
```

# Create volume group and logical volume
## Create volume group
Please note that the following commands will destroy all existing data on /dev/sdb.
1. First create a partition.
    ```
    # sgdisk -N 1 /dev/sdb
    ```
2. Create a Physical Volume (PV) without confirmation and 250K metadatasize.
    ```
    # pvcreate --metadatasize 250k -y -ff /dev/sdb1
    ```
3. Create a volume group named “vmdata” on /dev/sdb1
    ```
    # vgcreate vmdata /dev/sdb1
    ```
## Create logical volume
This can be easily done by creating a new thin LV:
```
# lvcreate -n <Name> -V <Size[M,G,T]> <VG>/<LVThin_pool>
```
A real world example:
```
# lvcreate -n vz -V 10G pve/data
```
Now a filesystem must be created on the LV:
```
# mkfs.ext4 /dev/pve/vz
```
At last this has to be mounted.
