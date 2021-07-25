# Configure vGPU in hyper-v

This works for only windows virtual machines

1. Turn off the virtual machine
   
2. Run powershell with Admin

3. $vm = "Name of my virtual machine"

4. Add VMGpuPartitionAdapter
    Add-VMGpuPartitionAdapter -VMName $vm

5. Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionVRAM 80000000 -MaxPartitionVRAM 100000000 -OptimalPartitionVRAM 100000000 -MinPartitionEncode 80000000 -MaxPartitionEncode 100000000 -OptimalPartitionEncode 100000000 -MinPartitionDecode 80000000 -MaxPartitionDecode 100000000 -OptimalPartitionDecode 100000000 -MinPartitionCompute 80000000 -MaxPartitionCompute 100000000 -OptimalPartitionCompute 100000000

6. Set-VM -GuestControlledCacheTypes $true -VMName $vm

7. Set-VM -LowMemoryMappedIoSpace 1Gb -VMName $vm

8. Set-VM -HighMemoryMappedIoSpace 32GB -VMName $vm

9.  虚拟机开机，从主机上复制C:\Windows\System32\DriverStore\FileRepository目录到虚拟机C:\Windows\System32\HostDriverStore\

    此时虚拟机上看到是这样的目录结构：C:\Windows\System32\HostDriverStore\FileRepository

    备注：HostDriverStore这个目录要自己创建，FileRepository里面本质上只要有主机显卡驱动就可以了，这里偷懒直接复制整个目录，如果只想复制主机显卡驱动目录，可以通过设备管理器查看主机加载的显卡驱动目录

10. 重启虚拟机，查看虚拟机设备管理器显卡，运行dxdiag查看显卡特性
