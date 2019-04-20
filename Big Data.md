# Big Data

* Big data is data larger than one can store on a system
* 5 V's - Value, Veracity, Velocity, Volume, Variety
* Data Lakes is the method of storing data to support the analysis of originally disparate sources of data
* Large volume of data coming from social networks, large company and mobiles
* 80% Data is unstructured

# Hadoop Fundamentals

* Open Source Project written in Java
* Uses Map Reduce
* Parallel Processing
* Distributed Computing
* Not Suitable for OLTP, OLAP, DSS
* Not a Replacement for RDBMS

## Hadoop Related Open Source Projects

* Eclipse - IDE for Java
* Lucene - Text Processing Library in Java
* HBase - Hadoop Database
* Hive - Data Warehousing Tools
* Pig - Generates MapReduce Commands (High Level Language)
* Spark - Cluster Computing Framework
* ZooKeeper- Centralized Configuration Service and Registry
* Ambari - Manage Hadoop Clusters through Web UI
* AVRO - Data Sterilization System
* UIMA - Architecture for managing unstructured data

## Hadoop Applications

* Super Computers and AI
* Processing Huge Data
* Data Storage
* Enterprise Search Technology
* Cloud Computing
* Business Analytics

## When Hadoop is not a good option

* Transaction Processing
* Non Parallizable workload
* Low Latency data access
* Processing lots of small files
* Not good for Intensive Calculations with little data

# Hadoop Architecture and HDFS

* Node -  A Computer
* Rack - Collection of nodes which are physically near and are connected to same network switch
* Cluster - Collection of Racks
* Hadoop uses 2 main components: HDFS and MapReduce Engine (Framework for performing calculations on data is a distributed file system)
* HDFS:
  * Runs on top of existing File System
  * Designed to handle very large files
  * Replication
  * No Random Access 
  * Uses file blocks - files in underlying FS (64-128MB)
  * If File Size is smaller than block size only needed size is used
  * Blocks can be larger than cluster size
  * Works well with replication
* MapReduce:
  * Consists of Map and Reduce transformation
  * Process huge Datasets
* HDFS Nodes: Name Node (Manage FS Namespace and FS Meta Data) and Data Node (Stores Blocks of Data)
* Map Reduce Nodes: Job Tracker (Manages MapReduce Jobs) and Task Tracker (Uses JVMs to run map reduce in parallel)
* YARN - MapReduce V2. Has Resource Manager and Scheduler
* Job and Task Trackers do not exist in YARN
* YARN Provides Efficient and Generic Scheduling and Resource Management.
* Hadoop 2 has 2 Name nodes, one active at a time
* Hadoop Federation allows horizontal growth
* As far as possible, Data is processed on a same rack

## HDFS Command Line

* File System shell can be invoked by using

```
hdfs dfs <args>
Ex: hdfs dfs -ls
```

* Uses common UNIX Commands
* FS commands can take path URLs as arguments
* There are some HDFS Specific 
  * copyFromLocal/put
  * copyToLocal/get
  * GetMerge - Get and Merge
  * setRep - replication level
* Ambari - Service status (GUI)

## Hands-on lab - Hadoop Architecture

This lab is recommended to be performed on the IBM Cloud using your previously created account Lab 1. 

\1. Log in IBM Cloud

Please use your account to log in [IBM Cloud](https://cocl.us/hadoop101-signup-ibm-cloud) and the resource dashboard is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-1.jpeg)

\2. Create IBM Analytics Engine

Click "**Catalog**"  and go to the page of IBM Cloud services, as shown below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-2.jpeg)

Choose "Analytics" => "Analytics Engine", it goes to configuration  of "Analytics Engine".  Please specify the instance name, like  'Hadoop-Lab2", and then

1) select a region/location to deploy in 

2) select a resource group

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-4.jpeg)

Then, click "Configure" and then set specify the parameters for your  hadoop cluster as shown below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-6.jpeg)

Choose number of compute nodes and software packages as the above by default to create a service.

***notice: It takes 30 to 60 minutes to start an Analytics Engine instance.***

Once an Analytics Engine service is created successfully,  it's displayed in your dashboard like the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-7.jpeg)

\3. Manage Hadoop in Ambari Console

Open your Hadoop cluster from dashboard and then click "Launch  Console"  to log in Ambari console using the provided username and  password in the red circle below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-10.jpeg)

After you log in Ambari console,  the Dashboard of your Hadoop cluster is shown as below : 

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-11.jpeg)

From the Dashboard, you are able to view all key metrics of your  Hadoop cluster nodes and manage various services, like YARN, HDFS, Hive,  etc.

\4.   HDFS management via command line

To manage files on HDFS in the command line , you need to be able to  log in the host from the remote ssh terminal .  Here are steps on how to  do it :

1)  Generate service credential for ssh

Open **Service credentials** on the left menu  like the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-12.jpeg)

 Then, in **Service credentials** page , please choose **New credential** button to generate a credential :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-13.jpeg)

select the values like the below to add a new credential:

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-14.jpeg)

Click '**Add**' button,  a new credential is generated and then find the information for ssh remote login :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-161.jpeg)

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-15.jpeg)

2) Log in a cluster node  via ssh

 From the above information, log in a cluster node via ssh client tool like [PuTTY](https://www.putty.org/) by providing username and password, like the below  :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-17.jpeg)

Now, you are able to run HDFS commands like  `**haddop fs -ls /**`  :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-18.jpeg)

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-19.jpeg)

# Hadoop Administration

* Adding or removing nodes can be done through Ambari web console
* We can see health of each node
* We can start or stop components
* Hadoop is configured using XML files
* hadoop-env.sh will set Env variables
* hdfs-site.xml is used to make main configuration changes
* topology should be scripted and script is referenced in topology.script.file.name in core-site.xml

## Hands-on lab - Hadoop ADMINISTRATION

This lab is recommended to be performed on the IBM Cloud using your previously created account Lab 1. 

\1. Log in IBM Cloud

Please use your account to log in [IBM Cloud](https://cocl.us/hadoop101-signup-ibm-cloud) and the resource dashboard is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-1.jpeg)

\2. Hadoop  Administration in Ambari Console

Open your Hadoop cluster from dashboard and  then click "Launch Console"  to log in Ambari console using the provided  username and password in the red circle below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-10.jpeg)

After you log in Ambari console,  the Dashboard of your Hadoop cluster is shown as below : 

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-11.jpeg)

From the Dashboard, you are able to view all  key metrics of your Hadoop cluster nodes and manage various services,  like YARN, HDFS, Hive, etc.

\3. HDFS 

If HDFS is chosen, metrics of HDFS is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-20.jpeg)

\4. YARN

If YARN is chosen, metrics of YARN is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-21.jpeg)

\5. MapReduce

If MapReduce is chosen, metrics of MapReduce is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-22.jpeg)

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-23.jpeg)

\6. Hive

If Hive is chosen, metrics of Hive is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-24.jpeg)

\7. Zookeeper

If Zookeeper is chosen, metrics of Zookeeper is shown as the below :

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-25.jpeg)

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-26.jpeg)

\8.  Ambari Metrics

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-27.jpeg)

![img](https://courses.cognitiveclass.ai/asset-v1:BigDataUniversity+BD0111EN+2016+type@asset+block/hdp-28.jpeg)

# Hadoop Components

## MapReduce

* Process Very Large Datasets
* Map - Partition input into smaller sub problems and distributes it into nodes
* Reduce - Take answers to sub problems and combine them to get the output.
*  Dependencies should not be present
* Uses Distributed MergeSort Engine
* Data Types: Key-Value Pairs and Lists
* Input (K1,V1) to Output list(K2,V2)

## Pig and Hive

* HLL to MapReduce
* Doesn't support low level tasks
* Pig
  * Data Flow Language (PigLatin)
  * Turing Complete with UDF, Relational Complete
  * Optional Schema
  * Local/Distributed Environments
  * pig script.pig
  * pig - commandline
  * call within java
* Hive :
  * HiveQL -SQL Dialect
  * Schema Required
  * Relationally Complete
  * hive ( shell)
  * hive -f script
  * hive -e 'Select * from mytable'

## Flume Sqoop and Oozie

* Flume - Moving Data, Gather log files from nodes in a cluster
  * Tiers- Agent, Collector, Storage

* Sqoop - Transfer data b/w RDBMS and Hadoop, Uses MapReduce and JDBC
* Oozie -  Job Control
  * Uses DAG
  * Definitions hPDL (XML Process Defination Language)