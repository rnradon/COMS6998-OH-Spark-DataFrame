# Spark SQL - DataFrames

A DataFrame is a _Dataset_ organized into named columns. Each column in a DataFrame has a name and an associated type. It is conceptually equivalent to a table in a relational database or a data frame in R/Python, but with richer optimizations under the hood.

We can build DataFrame from different data sources. For Example structured data file, tables in Hive, external databases or existing RDDs. The Application Programming Interface (APIs) of DataFrame is available in various languages such as Scala, Java, Python, and R.  

## Why DataFrames?
1. When there is not much storage space in memory or on disk, RDDs do not function properly as they get exhausted. 

2. RDDs store both structured and unstructured data together, which is not very efficient.

4. RDDs cannot modify the system in such a way that it runs more efficiently.  Further, they use **serialization**  (converting an object into a stream of bytes to allow faster processing) and  **garbage collection**  (an automatic memory management technique that detects unused objects and frees them from memory) techniques. This increases the overhead on the memory of the system as they are very lengthy.

Thus, to overcome these limitations of RDD, Spark DataFrames came into use.

## Let's perform some operations

Initialize SparkContext by:
`spark-shell` 
**SQLContext** (enables applications to run SQL queries programmatically and returns the result as a DataFrame) is a class and is used for initializing the functionalities of Spark SQL. SparkContext class object (sc) is required for initializing SQLContext class object.

Now let's create SQLContext

    scala> val sqlcontext = new org.apache.spark.sql.SQLContext(sc)

Read the JSON file and create a dataframe:

    scala> val df = sqlcontext.read.json("ta.json")
View the dataframe by:

    scala> df.show()
	
Select a column:

    df.select("name").show()

Filter operation: Show the list of TAs who take OH on "Monday"

    df.filter(df("day") === "Monday").show()
    

## Key Features of DataFrame

Here is a set of few characteristic features of DataFrame −

-   Ability to process the data in the size of Kilobytes to Petabytes on a single node cluster to large cluster.
    
-   Supports different data formats (Avro, csv, elastic search, and Cassandra) and storage systems (HDFS, HIVE tables, mysql, etc).
 
    
-   Can be easily integrated with all Big Data tools and frameworks via Spark-Core.
    
-   Provides API for Python, Java, Scala, and R Programming.
