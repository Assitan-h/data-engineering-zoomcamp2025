# Data Warehousing : 
OLAP VS OLTP:

![OLAP-OLTP](https://github.com/user-attachments/assets/80a9fd44-3167-44df-b67b-52058d5ac797)
![Screenshot 2025-02-05 204010](https://github.com/user-attachments/assets/bfbe409e-8623-4139-a81c-a3b25fb187c0)


## What is data 
Warehousing
OLAP Solution
Used for reporting and data analysis 

![Screenshot 2025-02-13 214058](https://github.com/user-attachments/assets/b53cf978-ef4c-457f-879a-51d2931bc42a)



## BigQuery : 
Serverless data warehouse : 

There are no servers to manage or database
Software as well as infrastructure including : 

Scalability and high-availability

Built-in features like : 

- Machine learning
- Geospatial analysis
- Business intelligence
      
BigQuery maximizes flexibility by separating the compute engine that analyzes your data from your storage

## BigQuery cost : 
- On demand pricing :

  1 TB of data processed

- Flare rate pricing:
  
    Based on number of pre requested slots
  
    100 slots - $2,000/month = 400 TB data processed on demand pricing
          
## Partition in BigQuery
Partition by (Cost efficiency, performance, …)

BigQuery partition : 

Time-unit column
Ingestion time(_PARTITIONTIME)
Integer range partitioning 
When using Time unit or ingestion time

-  daily (Default)
-  Hourly 
- Monthly or yearly
- Number of partitions limit is 4000

BigQuery Clustering  

Columns you specify are used to colocate related data 
Order of the column is important
The order of the specified columns determines the sort order of the data
Clustering improves :

 -  Filter queries
 - Aggregate queries
 - Table with data size inferior to 1GB, don’t show significant improvement with partitioning and clustering 
 - You can specify up to four clustering columns 

Clustering columns must be top-level, non-repeated columns
DATE
BOOL
GEOGRAPHY
INT64
NUMERIC
BIGNUMERIC
STRING
TIMESTAMP
DATETIME

## Partitioning vs Clustering : 


![Screenshot 2025-02-05 214154](https://github.com/user-attachments/assets/84d99a3e-9644-43a0-899a-92bb253e3ed4)

## Clustering over partitioning : 


- Partitioning results in a small amount of data per partition (approximately less than 1 GB)
- Partitioning results in a large number of partitions beyond the limits on partitioned tables
- Partitioning results in your mutation operations modifying the majority of partitions in the table frequently (for example, every few minutes)

## Automatic reclustering : 

As data is added to a clustered table 

- The newly inserted data can be written to blocks that contain key ranges that overlap with the key ranges in previously written blocks 
- These overlapping keys weaken the sort property of the table 
- To maintain the performance characteristics of clustered table
  
BigQuery performs automatic re-clustering in the background to restore the sort property of the table.
For partitioned tables, clustering is maintained for data within the scope of each partition. 
  
## BigQuery best practice : 

Cost reduction : 
- Avoid SELECT*
- Price your queries before running them
- Use clustered or partitioned tables 
- Use streaming inserts with caution
- Materialize query results in stages

## Query performance : 

- Filter on partitioned columns 
- Denormalizing data 
- Use nested or repeated columns 
- Use external data sources appropriately
- Don’t use it, in case  you want a high query performance
- Reduce data before using a JOIN 
- Do not treat WITH clauses as prepared statements
- Avoid oversharing tables

## Query performance : 

- Avoid JavaScript user-defined functions
- Use approximate aggregation functions(HyperLogLog++)
- Order Last, for query operations to maximize performance
- Optimize your join patterns
  
As a best practice, place the table with the largest number of rows first, followed by the table with the fewest rows, and then place the remaining tables by decreasing size.

![Screenshot 2025-02-06 183915](https://github.com/user-attachments/assets/3437427e-4ac0-4a16-a92d-e5f622995aa9)

![Screenshot 2025-02-06 184016](https://github.com/user-attachments/assets/5ae627be-a338-42d2-a959-4c8de929056c)

![Screenshot 2025-02-06 184046](https://github.com/user-attachments/assets/b72f2b44-8122-4d32-801f-2f6feb069804)


## ML in BigQuery pricing
Target audience Data analysts, managers
No need for python or java Knowledge
No need to export data into a different system

Free:

 - 10 GB per month of data storage 
 - 1 TB per month of queries processed
 - ML Create model step: First 10 GB per month is free

![Screenshot 2025-02-06 203619](https://github.com/user-attachments/assets/b2e0ce4b-8f5e-4a02-a46e-e9f75b6cdba2)

   
![Screenshot 2025-02-06 203645](https://github.com/user-attachments/assets/3325d106-6289-4b4f-90a5-53af252c13fd)

![Screenshot 2025-02-06 204632](https://github.com/user-attachments/assets/2cf5fac9-4d89-42bc-aabb-a1572704383b)



