# Hadoop configuration and launch scripts

For Hadoop we provide configuration templates for the `core-site.xml`, `hdfs-site.xml`, `mapreduce-site.xml`, and `yarn-site.xml` files. In addition, a launch script is provided to automate the deployment of Hadoop on a set of nodes.

# Configuration details

The included configuration sets a number of paths to sensible defaults for the DAS-4, and specifies container and memory sizes that work with the DAS. Notable settings include:

* All HDFS data and data of various daemons is placed in the `/local/$USER/hadoop/` directory.
* YARN is allocated 22 GB of memory per node, which is allocated in 1 GB chunks.
* MapReduce is configured to use 2 GB per mapper and 4 GB per reducer, of which 512 MB per task is reserved for I/O buffers.

# Launching hadoop

The `launch-hadoop-2.4` script can be used to deploy a Hadoop 2.4 cluster. The script takes as its inputs the directory containing a hadoop distribution, and a list of master node IP and slave node IPs. On each node the `/local/$USER/hadoop/` directory is cleared to ensure that a new, empty HDFS deployment can be set up. Afterwards, both HDFS and YARN are deployed to the specified nodes. For example, to deploy Hadoop on a set of nodes reserved using `preserve`, run from the root of this repository:

```
# Warning: this will wipe /local/$USER/hadoop/ on all reserved nodes!
bin/preserve-to-node-ips | hadoop/launch-hadoop-2.4 $HADOOP_HOME
```

Note that `$HADOOP_HOME` must point to the root of a Hadoop 2.4 distribution, and must be on a network-mounted filesystem that is accesible in the same directory on all nodes, such as your home directory or `/var/scratch/`.

