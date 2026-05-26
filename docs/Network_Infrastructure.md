# 2. Network Infrastructure

To ensure efficient data exchange during high-performance simulations, the cluster utilizes a dedicated private network architecture. This separates heavy research traffic from standard office or home network activity.

## Simple Overview: The Private Highway
Think of the cluster network as a private, high-speed highway dedicated exclusively to the cluster. 
* **Management Traffic:** The Headnode uses the public network for updates and external access.
* **Research Traffic (The Private Highway):** Worker Nodes communicate with the Headnode and each other over a dedicated, isolated network switch. This prevents network congestion and ensures that simulations run at maximum speed regardless of other network usage.



## Thorough Technical Details
* **Network Topology:** All nodes are physically connected to a managed Gigabit Ethernet switch. This ensures low-latency communication, which is critical for MPI-based (Message Passing Interface) research software like Quantum ESPRESSO.
* **Addressing Strategy:**
    * **Static Allocation:** Each node is assigned a permanent, non-dynamic IP address. This is critical for the Slurm scheduler, which requires stable addresses to route tasks reliably.
    * **Placeholder Addressing:** In this documentation, we follow the convention of `10.0.0.X` for private cluster nodes. 
    * *Implementation Table:*
        | Node Role | IP Address (Placeholder) |
        | :--- | :--- |
        | Headnode | `10.0.0.1` |
        | Worker Node 01 | `10.0.0.10` |
        | Worker Node 02 | `10.0.0.11` |
        *(Replace these with your specific internal static IP assignments.)*
* **Network Isolation:** By maintaining a dedicated subnet (`255.255.255.0`), we create a secure, isolated boundary for cluster data, reducing the risk of external interference and enhancing overall cluster stability.
