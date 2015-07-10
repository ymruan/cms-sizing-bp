
# JVM Setting and Tuning

### JVM Max Heap Size for UCMDB
One method for sizing the host machine's(physical or VM) memory os tp take the sum of the following:
1. Space for the guest operating system.(This can be 512 MB for Linux or 1 GB for a Windows OS, for example)
2. Space for the maximum number of java threads multiplied by the thread stack size
3. Additional memory for any other programs that are running in the same guest operating syste (In oder to get a better performance, we don't recommend to install the other programms on the same guest OS)
4. Space for the JVM maximum heap size



You can configure the max heap size in UCMDB-installation-folder/bin/wrapper-platform.conf.

We recommended to set the 24 GB as the max heap size for the UCMDB Server

```
wrapper.java.initmemory=24096
wrapper.java.maxmemory=24096
```



### The G1 Garbage Collector
Start from UCMDB 10.21. UCMDB Server use G1 as the OOTB Garbage Collector. In oder to gain the better performance, we recommend to upgrade the UCMDB to 10.21.

The Garbage-First (G1) collector is a server-style garbage collector, targeted for multi-processor machines with large memories. It meets garbage collection (GC) pause time goals with a high probability, while achieving high throughput. The G1 garbage collector is fully supported in Oracle JDK 7 update 4 and later releases. The G1 collector is designed for applications that:

* Can operate concurrently with applications threads like the CMS collector.
* Compact free space without lengthy GC induced pause times.
* Need more predictable GC pause durations.
* Do not want to sacrifice a lot of throughput performance.
* Do not require a much larger Java heap.

G1 is planned as the long term replacement for the Concurrent Mark-Sweep Collector (CMS). Comparing G1 with CMS, there are differences that make G1 a better solution. One difference is that G1 is a compacting collector. G1 compacts sufficiently to completely avoid the use of fine-grained free lists for allocation, and instead relies on regions. This considerably simplifies parts of the collector, and mostly eliminates potential fragmentation issues. Also, G1 offers more predictable garbage collection pauses than the CMS collector, and allows users to specify desired pause targets.



### How to setup G1 gc and G1 gc tuning
Start from UCMDB 10.21. UCMDB Server use the G1 as the OOTB GC. If you want to configure the UCMDB to use the G1 GC, here is the configuration for you reference.


