# 1. Hardware Foundation

This cluster is built on a distributed architecture, using a single **Headnode** as the master controller and multiple **Worker Nodes** as the computational workhorses.

* **Physical Server Racking and Power Management:** The cluster is organized within a standardized server rack to ensure efficient cooling and cable management. All nodes are connected to managed Power Distribution Units (PDUs), ensuring that power delivery is stable and that we can monitor energy usage across the entire rack from a centralized interface.

* **Node Roles and Hierarchy:** The cluster operates on a master-worker architecture:
    * **Headnode (Master):** Serves as the central command center. It manages the Slurm scheduler, hosts the shared research data, and provides the environment for submitting and monitoring jobs.
    * **Worker Nodes (Pool):** Functions as a scalable compute pool. These nodes receive instructions from the Headnode to execute high-performance simulations in parallel, allowing us to process complex materials science calculations significantly faster than a single machine.
