# Configure vGPU in hyper-v

This works for only windows virtual machines

1. Turn off the virtual machine
   
2. Run powershell with Admin

3. $vm = "Name of my virtual machine"

4. Add VMGpuPartitionAdapter
    ```
    Add-VMGpuPartitionAdapter -VMName $vm
    ```

5. Set VMGpuPartitionAdapter
    ```
    Set-VMGpuPartitionAdapter -VMName $vm -MinPartitionVRAM 80000000 -MaxPartitionVRAM 100000000 -OptimalPartitionVRAM 100000000 -MinPartitionEncode 80000000 -MaxPartitionEncode 100000000 -OptimalPartitionEncode 100000000 -MinPartitionDecode 80000000 -MaxPartitionDecode 100000000 -OptimalPartitionDecode 100000000 -MinPartitionCompute 80000000 -MaxPartitionCompute 100000000 -OptimalPartitionCompute 100000000
    ```

6. Set VM
    ```
    Set-VM -GuestControlledCacheTypes $true -VMName $vm
    Set-VM -LowMemoryMappedIoSpace 1Gb -VMName $vm
    Set-VM -HighMemoryMappedIoSpace 32GB -VMName $vm
    ```

7.  Turn on the virtual machine, copy the folder "C:\Windows\System32\DriverStore\FileRepository" from the host into the folder "C:\Windows\System32\HostDriverStore\" on the virtual machine

    Then you can the the current folder tree like this on the virtual machine：C:\Windows\System32\HostDriverStore\FileRepository

    Note：You should create the foleder "HostDriverStore" by yourself.

8.  Restart the virtual machine, check the GPU in the Device Manager.
9.  You could run the follows to check the graphic cards properties:
    ```
    dxdiag
    ```