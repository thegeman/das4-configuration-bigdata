# das4-configuration-bigdata

This repository contains a collection of launch scripts and default configurations specific to the DAS-4 for a variety of big data platforms and software.

# Reserving nodes on DAS-4

To run big data applications on DAS-4 nodes, a user has to reserve nodes for a specified amount of time using the `preserve` command. For example, to reserve 5 nodes for 15 minutes:

```
preserve -np 5 -t 15:00
```

Using `bin/preserve-to-node-ips` you can obtain a list of IP addresses of the nodes you reserved.

# Supported software

Below is a list of supported software. Note that the listed versions are the versions that have been tested. Other versions are likely to work if they are minor version changes.

* [Hadoop](hadoop/README.md) (version 2.4.1)
* [ZooKeeper](zookeeper/README.md) (version 3.4.6)

