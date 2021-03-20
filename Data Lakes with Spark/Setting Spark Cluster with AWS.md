## EC2 vs EMR

- |AWS EMR |	AWS EC2
---|----|---------
Distributed computing |	Yes	|Yes
Node categorization |	Categorizes secondary nodes into core and task nodes as a result of which data can be lost in case a data node is removed. |	Does not use node categorization
Can support HDFS? |	Yes	|Only if you configure HDFS on EC2 yourself using multi-step process.
What protocol can be used? |	Uses S3 protocol over AWS S3, which is faster than s3a protocol	| ECS uses s3a
Comparison cost|	Bit higher	|Lower
#


## Circling back about HDFS

Previously we have looked over the Hadoop Ecosystem. To refresh those concepts, we have provided reference material here. HDFS (Hadoop Distributed File System) is the file system. HDFS uses MapReduce system as a resource manager.

Spark can replace the MapReduce algorithm. Since Spark does not have its own distributed storage system, it leverages using HDFS or AWS S3, or any other distributed storage. Primarily in this course, we will be using AWS S3, but let’s review the advantages of using HDFS over AWS S3.

## What is HDFS?

HDFS (Hadoop Distributed File System) is the file system in the Hadoop ecosystem. Hadoop and Spark are two frameworks providing tools for carrying out big-data related tasks. While Spark is faster than Hadoop, Spark has one drawback. It lacks a distributed storage system. In other words, Spark lacks a system to organize, store and process data files.

## MapReduce System

HDFS uses MapReduce system as a resource manager to allow the distribution of the files across the hard drives within the cluster. Think of it as the MapReduce System storing the data back on the hard drives after completing all the tasks.

Spark, on the other hand, runs the operations and holds the data in the RAM memory rather than the hard drives used by HDFS. Since Spark lacks a file distribution system to organize, store and process data files, Spark tools are often installed on Hadoop because Spark can then use the Hadoop Distributed File System (HDFS).

## Why do you need EMR Cluster?
Since a Spark cluster includes multiple machines, in order to use Spark code on each machine, we would need to download and install Spark and its dependencies. This is a manual process. Elastic Map Reduce is a service offered by AWS that negates the need for you, the user, to go through the manual process of installing Spark and its dependencies for each machine.

## Setting up AWS
Please refer to the latest [AWS documentation to set up an EMR Cluster](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html#emr-getting-started-plan-and-configure).

Let’s pause to do a quick check for understanding from a previous page.


## AWS CLI - Create EMR Cluster

Let's learn how to create an EMR cluster from the CLI, and configure the related settings.

1. ```aws emr create-cluster``` command

While creating EMR through AWS console has been shown, but if you know your instances' specificity, such as which applications you need or what kind of clusters you’ll need, you can reuse the aws emr ```create-cluster command``` below multiple times.

```
aws emr create-cluster --name <cluster_name> \
 --use-default-roles --release-label emr-5.28.0  \
--instance-count 3 --applications Name=Spark Name=Zeppelin  \
--bootstrap-actions Path="s3://bootstrap.sh" \
--ec2-attributes KeyName=<your permission key name> \
--instance-type m5.xlarge --log-uri s3:///emrlogs/
```

Options of the aws emr create-cluster command - Let’s break down the command and go over each option to know its responsibility.

**--name :** You can give any name of your choice. This will show up on your AWS EMR UI.

**--release-label:** This is the version of EMR you’d like to use.

--instance-count: Annotates instance count. One is for the primary, and the rest are for the secondary. For example, if --instance-count is given 4, then 1 instance will be reserved for primary, then 3 will be reserved for secondary instances.

**--applications:** List of applications you want to pre-install on your EMR at the launch time

**--bootstrap-actions:**The Path attribute provides the path to a file (residing in S3 or locally) that contains a script that runs during a bootstrap action. The script may set environmental variables in all the instances of the cluster. This file must be accessible to each instance in the cluster.

**--ec2-attributes KeyName:** Specify your permission key name, for example, if it is MyKey.pem, just specify MyKey for this field

**--instance-type:** Specify the type of instances you want to use. Detailed list can be accessed here, but find the one that can fit your data and your budget.

**--log-uri:** S3 location to store your EMR logs in. This log can store EMR metrics and also the metrics/logs for submission of your code.