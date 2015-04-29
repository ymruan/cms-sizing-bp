# Sizing definiation and Recommendation

When planning capacity, among other issues, you should consider the ratio of managed nodes in your CMDB to node-related CIs. Node-related CIs include all CIs of types which are subclasses of Application Resource, Node Element, or Running Software.

The following table lists the number of node-related CIs you can discover for each managed node in your environment. This number depends on the size of your deployment and the number of managed nodes (the more managed nodes you maintain in the CMDB, the fewer node-related CIs you can discover for each managed node).

For example, in an Enterprise deployment if you are running 134,400 managed nodes, you can discover 160 node-related CIs for each managed node. If you are running only 43,200 managed nodes, you can discover 500 resource CIs for each managed node.

**Note:** The number used in managed nodes is only CIs and not relationships.






### uCMDB Probe Server Sizing - Introduction

**Small deployment**: A Small deployment supports a biweekly scanner-based inventory of 7500 nodes or a daily discovery of 5000 nodes for application dependency mapping. Other combinations of scanner based inventory nodes and application dependency mapping discovery nodes are also supported, according to the following formula:

[The number of Inventory Discovery nodes] + 5 times [the number of application dependency mapping nodes] is less than or equal to 7500.

**Standard deployment** : A Standard deployment supports a biweekly scanner-based inventory of 25000 nodes or a daily discovery of 5000 nodes for application dependency mapping. Other combinations of scanner based inventory nodes and application dependency mapping discovery nodes are also supported, according to the following formula:

[The number of Inventory Discovery nodes] + 5 times [the number of application dependency mapping nodes] is less than or equal to 25000.

**Enterprise deployment** : An Enterprise deployment supports a biweekly scanner-based inventory of 75000 nodes or a daily discovery of 10000 nodes for application dependency mapping. Other combinations of scanner based inventory nodes and application dependency mapping discovery nodes are also supported, according to the following formula:

[The number of Inventory Discovery nodes] + 7.5 times [the number of application dependency mapping nodes] is less than or equal to 75000.

For example, 15000 inventory discovery nodes and 2000 application dependency mapping nodes, in a Standard deployment, would be supported. The XML Enricher must be configured to match the deployment mode of the probe.
