# UCMDB Max Capacity and Performance Recommendation for Database


Database responsiveness is critical for the CMS application. CMS is a typical OLTP application where it demand good read/write from responsive DB. It is good practice for the Database admin to identify workloads and plan the DB online maintenance scripts.

Lets assume a scenario where a db insert query is slow and you would like to understand the DB bottleneck. First identify if it is an infrastructure issue ( CPU/MEM bottleneck, IO bottleneck ..). If not you need to look for DB performance bottle neck items like...

Temp db bottlenecks
Transaction log bottlenecks deadlocks
Indexing issues.
Always use the database requirement guide as a validator to check if you have the database server setup properly. Before CMS server goes for production, make sure the DB Admin has monitoring enabled and is capturing all required metrics for effective Analysis. If you have products like HP OM Agent with Oracle SPI, the agent will have some OOTB policies to capture the DB metrics which can then be visualized via HP Performance Manager.

If you have oracle installed on unix machine which has OV Performance Agent, then you can customize the parm (/var/opt/perf/parm) file to get oracle related process information.

## Database # Max CI support
The UCMDB Server's max capacity suport for different database
* Oracle - 60M CIs+Relationships
* MS SQL Server - 40M CIs+Relationships


##Database Performance Recommendation
* Database Server Must be a physical machine.It should be an independent server witout other application running on it
* Database Server should be in the same sub-net as UCMDB Server, to ensure the network latency to be less than 1 ms.
* The I/O thoughput on the database server shoudl be 200M/b
* Use Oracle database instead of MSSQL Server. If is not possible to use Oracle, please use MS SQL Enterprise edition instead of Standard edition
* Do not place data or log files on the same disk
* Recommended to use a fault tolerant disk ideally. RAID1, RAID0+1 is recommended for database files because it avoids hot spots. If RAID 0 does not provide protection against failure. It require a strong backup strategy
* Use SSD for improve the IO read/write performance
* Upgrade the current Oracle from Oracle 11 to Oracle 12, MS SQL 2012 to 2014 can improve the performance
*

## Hardware recommendation for Database
| Deployment | Number of Processor (Minimum/Recommend) |  Memory  (Minimum/Recommend)|
| -- | -- | -- |
| Enterprise | 24 Cores| 64 GB |


##Apendix
##UCMDB System Benchmark Test Results on Oracle 12

https://rndwiki2.atlanta.hp.com/confluence/display/mam/CMS_10_20_60M_NoSearch_Oracle12_12hour_3rdRound

##UCMDB System Benchmark Test Results on MSSQL 2014
https://rndwiki2.atlanta.hp.com/confluence/display/mam/CMS_10_20_40M_NoSearch_MSSQL2014_12hour













