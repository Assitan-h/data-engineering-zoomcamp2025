# Data Warehousing : 
OLAP VS OLTP:

## What is data Warehousing
OLAP Solution
Used for reporting and data analysis 

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

Partitioning vs Clustering : 

## Clustering over partitioning : 

Partitioning results in a small amount of data per partition (approximately less than 1 GB)
Partitioning results in a large number of partitions beyond the limits on partitioned tables
Partitioning results in your mutation operations modifying the majority of partitions in the table frequently (for example, every few minutes)

## Automatic reclustering : 
 As data is added to a clustered table 
The newly inserted data can be written to blocks that contain key ranges that overlap with the key ranges in previously written blocks 
These overlapping keys weaken the sort property of the table 
To maintain the performance characteristics of clustered table
BigQuery performs automatic re-clustering in the background to restore the sort property of the table
For partitioned tables, clustering is maintained for data within the scope of each partition. 
  
## BigQuery best practice : 

   Cost reduction : 
   Avoid SELECT*
   Price your queries before running them
   Use clustered or partitioned tables 
   Use streaming inserts with caution
   Materialize query results in stages

## Query performance : 
Filter on partitioned columns 
Denormalizing data 
Use nested or repeated columns 
Use external data sources appropriately
Don’t use it, in case  you want a high query performance
Reduce data before using a JOIN 
Do not treat WITH clauses as prepared statements
Avoid oversharing tables

## Query performance : 
Avoid JavaScript user-defined functions
Use approximate aggregation functions(HyperLogLog++)
Order Last, for query operations to maximize performance
Optimize your join patterns
As a best practice, place the table with the largest number of rows first, followed by the table with the fewest rows, and then place the remaining tables by decreasing size.


## ML in BigQuery pricing
Target audience Data analysts, managers
No need for python or java Knowledge
No need to export data into a different system

Free:

 - 10 GB per month of data storage 
 - 1 TB per month of queries processed
 - ML Create model step: First 10 GB per month is free



