
# Reading Notes
## Class 12
_____________________________________________________________________________________________________________________________________


### SQL vs NoSQL

- SQL databases are primarily called as Relational Databases (RDBMS); whereas NoSQL database are primarily called as non-relational or distributed database.

- SQL databases are table based databases whereas NoSQL databases are document based, key-value pairs, graph databases or wide-column stores.

- SQL databases have predefined schema whereas NoSQL databases have dynamic schema for unstructured data.

- SQL databases are vertically scalable whereas the NoSQL databases are horizontally scalable. SQL databases are scaled by increasing the horse-power of the hardware. NoSQL databases are scaled by increasing the databases servers in the pool of resources to reduce the load.

- For properties: SQL databases emphasizes on ACID properties ( Atomicity, Consistency, Isolation and Durability) whereas the NoSQL database follows the Brewers CAP theorem ( Consistency, Availability and Partition tolerance )


### NoSQL database example

- Mongodb is one of the most popular document based NoSQL database as it stores data in JSON like documents. It is non-relational database with dynamic schema.
- Speed: For simple queries, it gives good performance, as all the related data are in single document which eliminates the join operations.
- Scalability: It is horizontally scalable i.e. you can reduce the workload by increasing the number of servers in your resource pool instead of relying on a stand alone resource.

- Manageable: It is easy to use for both developers and administrators. This also gives the ability to shard database
- Dynamic Schema: Its gives you the flexibility to evolve your data schema without modifying the existing data

### NOSQL DATA MODELING TECHNIQUES

![nosql](https://highlyscalable.files.wordpress.com/2012/02/overview2.png)
![](https://highlyscalable.files.wordpress.com/2012/02/soft-schema2.png)
![](![image](https://user-images.githubusercontent.com/63610157/116273152-5d47ef00-a736-11eb-85de-fabe0eb2a0c7.png)
