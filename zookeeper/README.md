# ZooKeeper configuration and launch scripts

For ZooKeeper, we provide a minimal configuration that launches a ZooKeeper service on the "master node" of a reservation, listening on port 2181 by default. A launch script is provided for the deployment of ZooKeeper on a `preserve` reservation.

# Launching ZooKeeper

The `launch-zookeeper-3.4` script can be used to deploy a ZooKeeper 3.4 server. The script connects to a single node, wipes the data of any previous ZooKeeper instances in `/local/$USER/zookeeper/`, and start a ZooKeeper instance. Note that this node is the node that would be used as Hadoop master, given a `preserve` reservation of nodes. Example usage of the script, run from the root of this repository:

```
# Warning: this will wipe /local/$USER/zookeeper/ on the first node in the reservation
bin/preserve-to-node-ips | zookeeper/launch-zookeeper-3.4 $ZOOKEEPER_HOME
```

Note that `$ZOOKEEPER_HOME` must point to the root of a ZooKeeper 3.4 distribution, and must be on a network-mounted filesystem that is accesible in the same directory on all nodes, such as your home directory or `/var/scratch/`.

