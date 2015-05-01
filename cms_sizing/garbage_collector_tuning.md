
# Garbage Collector Tuning


#### The G1 Garbage Collector


The Garbage-First (G1) collector is a server-style garbage collector, targeted for multi-processor machines with large memories. It meets garbage collection (GC) pause time goals with a high probability, while achieving high throughput. The G1 garbage collector is fully supported in Oracle JDK 7 update 4 and later releases. The G1 collector is designed for applications that:

* Can operate concurrently with applications threads like the CMS collector.
* Compact free space without lengthy GC induced pause times.
* Need more predictable GC pause durations.
* Do not want to sacrifice a lot of throughput performance.
* Do not require a much larger Java heap.

G1 is planned as the long term replacement for the Concurrent Mark-Sweep Collector (CMS). Comparing G1 with CMS, there are differences that make G1 a better solution. One difference is that G1 is a compacting collector. G1 compacts sufficiently to completely avoid the use of fine-grained free lists for allocation, and instead relies on regions. This considerably simplifies parts of the collector, and mostly eliminates potential fragmentation issues. Also, G1 offers more predictable garbage collection pauses than the CMS collector, and allows users to specify desired pause targets.
### Recommended Use Cases for G1

The first focus of G1 is to provide a solution for users running applications that require large heaps with limited GC latency. This means heap sizes of around 6GB or larger, and stable and predictable pause time below 0.5 seconds.

Applications running today with either the CMS or the ParallelOldGC garbage collector would benefit switching to G1 if the application has one or more of the following traits.

* Full GC durations are too long or too frequent.
* The rate of object allocation rate or promotion varies significantly.
* Undesired long garbage collection or compaction pauses (longer than 0.5 to 1 second)

**Note:** If you are using CMS or ParallelOldGC and your application is not experiencing long garbage collection pauses, it is fine to stay with your current collector. Changing to the G1 collector is not a requirement for using the latest JDK.


Best Practices

There are a few best practices you should follow when using G1.

Do not Set Young Generation Size

Explicitly setting young generation size via -Xmn meddles with the default behavior of the G1 collector.

G1 will no longer respect the pause time target for collections. So in essence, setting the young generation size disables the pause time goal.
G1 is no longer able to expand and contract the young generation space as needed. Since the size is fixed, no changes can be made to the size.
Response Time Metrics

Instead of using average response time (ART) as a metric to set the XX:MaxGCPauseMillis=<N>, consider setting value that will meet the goal 90% of the time or more. This means 90% of users making a request will not experience a response time higher than the goal. Remember, the pause time is a goal and is not guaranteed to always be met.

What is an Evacuation Failure?

A promotion failure that happens when a JVM runs out of heap regions during the GC for either survivors and promoted objects. The heap can't expand because it is already at max. This is indicated in the GC logs when using -XX:+PrintGCDetails by to-space overflow. This is expensive!

GC still has to continue so space has to be freed up.
Unsuccessfully copied objects have to be tenured in place.
Any updates to RSets of regions in the CSet have to be regenerated.
All of these steps are expensive.
How to avoid Evacuation Failure

To avoid evacuation failure, consider the following options.

Increase heap size
Increase the -XX:G1ReservePercent=n, the default is 10.
G1 creates a false ceiling by trying to leave the reserve memory free in case more 'to-space' is desired.
Start the marking cycle earlier
Increase the number of marking threads using the -XX:ConcGCThreads=n option.
Complete List of G1 GC Switches



a blog for G1 tuning
http://www.oracle.com/technetwork/articles/java/g1gc-1984535.html
