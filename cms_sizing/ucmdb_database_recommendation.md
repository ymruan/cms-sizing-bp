# UCMDB Database Recommendation
##Common Recommendation
* Database Server Must be a physical machine.It should be an independent server witout other application running on it
* Database Server should be in the same sub-net as UCMDB Server, to ensure the network latency to be less than 1 ms.
* The I/O thoughput on the database server shoudl be ?????
* Use Oracle database instead of MSSQL Server. If is not possible to use Oracle, please use MS SQL server BI or Enterprise edition instead of Standard edition
* Do not place data or log files on the same disk
* Recommended to use a fault tolerant disk ideally. RAID1, RAID0+1 is recommended for database files because it avoids hot spots. If RAID 0 does not provide protection against failure. It require a strong backup strategy
* Use SSD for improve the IO read/write performance
* Upgrade the current Oracle from Oracle 11 to Oracle 12, MS SQL 2012 to 2014 can improve the performance
*

## Hardware recommendation for Oracle
| Deployment | Number of Processor |  Memory |
| -- | -- | -- |
| Small| Small <br />Recommended| Small <br />Recommended|
| Large | Small <br />Recommended | Small <br />Recommended |




## Hardware recommenation for MSSQL

| Deployment | Number of Processor |  Memory |
| -- | -- | -- |
| Small | Small <br />Recommended | Small <br />Recommended |
| Large | Small <br />Recommended | Small <br />Recommended |















