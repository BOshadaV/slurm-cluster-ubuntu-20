# 3. Distributed Filesystem

To ensure seamless access to research data and software across the cluster, we utilize an NFS (Network File System) architecture. This allows the Worker Nodes to mount central directories hosted on the Headnode as if they were local disks.

## Simple Overview: The Shared Library
Think of the Headnode as a library. Instead of every worker node having its own copy of every book (software or data), they all connect to the library's shelf. 
* **Shared Apps (`/opt/apps`):** All software binaries are installed once on the Headnode. When a node runs a job, it executes the binary directly from this shared mount.
* **Shared Research Data (`/mnt/mphil_disk`):** All input pseudopotentials and output simulation data reside here, allowing for real-time monitoring and analysis from any node.

## Thorough Technical Details


### 3.1 NFS Server Setup (Headnode)
The Headnode exports the necessary directories via `/etc/exports`. 
* Ensure the export permissions are restricted to your specific cluster subnet to maintain security.
* Example configuration:
  `/path/to/shared/data  [CLUSTER_SUBNET_RANGE](rw,sync,no_subtree_check)`

### 3.2 Client-side Mounting (Worker Nodes)
Each Worker Node mounts the Headnode exports during boot. To ensure stability during reboots, we use the `_netdev` and `nofail` mount options in `/etc/fstab`.

* **The Fstab Configuration:**
  `[HEADNODE_IP]:/path/to/shared/data  /mount/point  nfs  defaults,_netdev,nofail  0  0`

* **Why these options matter:**
    * `_netdev`: Tells the system to wait until the network is fully initialized before attempting to mount the storage.
    * `nofail`: Prevents the system from hanging or failing to boot if the Headnode is offline or the network connection is interrupted.

### 3.3 Verification
After configuring, use these commands on a Worker Node to verify the connection:
1. `mount -a` (To test the new fstab entries).
2. `df -h` (To confirm the remote storage is correctly visible and has the expected capacity).
