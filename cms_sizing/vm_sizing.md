# VM Sizing

CMS can be deployed in both physical and virtualized environments. The following virtual environments are supported.

The following table lists the number of node-related CIs you can discover for each managed node in your environment. This number depends on the size of your deployment and the number of managed nodes (the more managed nodes you maintain in the CMDB, the fewer node-related CIs you can discover for each managed node).

* VMWare ESX, VMWare ESXi
* Microsoft Hype-V

If virtual servers are being used for a production CMS system, HP recommends:

1.
It is highly recommended that you use **physical hardware for UCMDB Database** in production environments where performance is a concern.

2.
Assign dedicated resources (such as vCPU, memory, and disk I/O) to a guest operating system that acts as a UCMDB and Probe Server.

3.
Deploy all UCMDB Server HA deployment in the **same virtualization resource pool**.

4.
Use the **high performance storage** (such like HP 3PAR) for UCMDB server (If the I/O is not good enough, with some user scenarios, such as SOLR full indexing, it might cause CPU high usage).

For the hardware recommendation, we recommend to use the same number of vCPU and memory as HP recommend for physical deployment. For example, in HP in lab performance, we use 8 vCPU for the test.
**VM Hardware**



* Latest generation of Intel/AMD processors recommend.
* Free hard disk space should more than 30G (for logs, memory dumps and so on)
* If the search functionality was enabled, it should use more hard disk space ( for example, 7M CIs
need 30G space for SOLR index files)
* Windows Virtual Memory = physical memory * 1.5
* Linux Swap = physical memory * 1
*

## Hardware Performance Issue

The hardware requirements for Hypervisors running CMS Core VMs can vary based on these factors:

* The availability of the physical CPUs and memory in the Hypervisor to support the recommended
CMS VM configuration.

* The number of VMs running concurrently on the physical server. For more information about
improving performance, click here

