# 5. First Computation

Once the infrastructure is up, the scheduler is running, and the storage is mounted, it is time to perform a "sanity check" to ensure the cluster is ready for production research.

## Simple Overview: The "Hello World" of HPC
Before running a complex materials science simulation, we run a short, lightweight test job. This confirms that:
1. **The Scheduler is working:** The Headnode can successfully send a task to a Worker Node.
2. **The Environment is configured:** The Worker Node can access the necessary software binaries and research files.
3. **The Computation is happening:** The Worker Node reports back with valid data.



## Thorough Technical Details

### 5.1 Preparing the Test Job Script
A Slurm job script is a bash script with special `#SBATCH` directives that tell the scheduler what resources are required.

* **Example `test_job.sh`:**
  ```bash
  #!/bin/bash
  #SBATCH --job-name=cluster_test
  #SBATCH --nodes=1
  #SBATCH --ntasks-per-node=4
  #SBATCH --output=results_%j.out

  # Run a simple check command or a short simulation script
  srun [PATH_TO_BINARY]/[EXECUTABLE_NAME] -in input_file.in
