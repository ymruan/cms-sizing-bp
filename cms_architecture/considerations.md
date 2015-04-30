# CMS Architecture Considerations

**Size of my enterprise :** Its all numbers. You need to have an idea of how many servers / network devices you have ? uCMDB/CMS product versions have different capacity boundaries. For ex, Current CMS with Oracle Database can handle 60 million Ci’s and relationships.

**Integration Points:** CMS is often the central point of focus in any reference architecture. Identifying critical integration points will help to design the architecture.

**Network Layout :** Every customer network segments are different. With Mergers and Acquisitions, its more fun !!! You will see different network topology adopted and preached. You are going to see one the below structures in your network.

* IP segmentation based on geo-clustering. Ex : Country specific.
* IP segmentation based on Datacenter location. Some architectures where spanning is enabled, it will
allow same IP segments across datacenters.
* PCI/DMZ and Other secure segments.
* Non routable islands where IP routing is not allowed.

**Network Latency:** Discovery is network driven. Understanding latency across network segments will help to plan the probe location.


