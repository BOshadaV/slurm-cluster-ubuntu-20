# slurm-cluster-ubuntu-20

This repository contains the documentation and configuration workflows for building a Slurm-managed compute cluster designed for high-performance scientific research, including Quantum ESPRESSO, Calypso, and Machine Learning calculations.

## The Road to Cluster
*Building a modular, scalable research compute environment.*

- [ ] **1. Hardware Foundation**
  - Physical server racking and power management.
  - Master-Worker node architecture roles.
- [ ] **2. Network Infrastructure**
  - Private "highway" network isolation.
  - Static IP configuration and subnet management.
- [ ] **3. Distributed Filesystem**
  - Setting up NFS for shared research data.
  - Mounting `/opt/apps` and storage volumes via `/etc/fstab`.
- [ ] **4. Scheduler & Management**
  - Munge authentication service setup.
  - Slurm Controller (`slurmctld`) and Node (`slurmd`) deployment.
- [ ] **5. First Computation**
  - Validating the cluster with an initial `sbatch` workload.
  - Monitoring resources with `squeue` and `sacct`.

---

## Troubleshooting Log
*A reference guide for common hurdles and their solutions.*
- Check the [Troubleshooting Log](./docs/TROUBLESHOOTING.md) for resolutions to common deployment errors.

## License
This project is licensed under the MIT License.
