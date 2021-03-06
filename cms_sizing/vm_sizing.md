# VM Sizing

CMS can be deployed in both physical and virtualized environments. The following virtual environments are supported.
* VMWare ESX, VMWare ESXi
 - 4.0, 4.1
 - 5.0, 5.0 update 1
* Microsoft Hype-V
 - 2008 R2 SP1
 - 2012

If virtual servers are being used for a production CMS system, HP recommends:

1.
It is highly recommended that you use **physical hardware for UCMDB Database** in production environments where performance is a concern.

2.
Assign dedicated resources (such as vCPU, memory, and disk I/O) to a guest operating system that acts as a UCMDB and Probe Server( set the "reservation" value).


3.
Deploy all UCMDB Server HA deployment in the **same virtualization resource pool**.

4.
Use the **high performance storage** (such like HP 3PAR) for UCMDB server (If the I/O is not good enough, with some user scenarios, such as SOLR full indexing, it might cause CPU high usage). Check the guest average(GAVG) and disk average(DAVG) latency time columns in the esxtop tool's output to ensure that your I/O system is not causing bottleneckes due to disk latencies

For the hardware recommendation, in oder to get an accurate result when comparing the performance of CMS on physical and virtual machine implementations, it is important to assign the same number of virtual CPUS to the ESX virtual machine as there are physical CPUs on the physical operating system. It is also necessary to assign the same amount of memory to the VM.Otherwise the comparison is not a true one.

ESX has three separate areas of memory overhead:
* A fixed system-wide overhead for the service console (273 MB for ESX 3.x)
* A fixed system-wide overhead for the VMKernel part of ESX. This overhead depends on the number and size of the device drivers contained in it.
* An additional overhead for each virtual machine. The virtual machine monitor requires a certain amount of memory for its code and data.

By sizing the virtual machine memory correclty for the processes with it, you can avoid the occurrence of guest operating system swapping due to memory pressure. If the guest operating system decides to swap out any part of the memory pages that makes up the JVM heap, then the UCMDB Server's performance will be affected. If the swapping is occuring, it can be seen using the operating system's own tool, such as "vmstat" on Linux and "perfmon" on Windows system.

