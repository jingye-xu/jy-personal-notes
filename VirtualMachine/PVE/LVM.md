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

## Create logical volume
