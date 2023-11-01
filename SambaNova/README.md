# Sambanova

## Connection to Sambanova 

Connection to a SambaNova node is a two-step process. The first step is to `ssh` to the `login node`. The second step is to log in to a SambaNova node from the `login node`.

![Sambanova connection diagram](./sambanova_login.jpg)

Login to the Sambanova login node from your local machine.  This uses the **MobilePASS+** token generated every time you log in to the system. 

In the examples below, replace ALCFUserID with your ALCF user id.
```bash
ssh ALCFUserID@sambanova.alcf.anl.gov
Password: < MobilePASS+ code >
```

Note: Use the ssh "-v" option in order to debug any ssh problems.

Once you are on the login node, ssh to one of the sambanova nodes.
```bash
ssh sn30-r1-h1       
```

You can also ssh to `sn30-r1-h1` , `sn30-r1-h2`, `sn30-r2-h1`, `sn30-r2-h2`, `sn30-r3-h1`, `sn30-r3-h2`, `sn30-r4-h1`, `sn30-r4-h2`.

## Pre-Built Sample Venv 

Sambanova software stack and associated environmental variables are automatically setup at login for a SN30 node. 

Each of the samples or application examples provided by SambaNova has its own pre-built virtual environment which can be readily used. They are present in the `/opt/sambaflow/apps/` directory tree within each of the applications. 

# Example 1 - Steps to run GPT 13B SS2k on SambaNova DataScale SN30 using 4 RDUs

**Note**: for the sake of the tutorial, we have precompiled the model and lowered the batch size and number of train steps to reduce the execution time.

1. Create a folder in your home repo, and copy the bash script `/projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss2k_run.sh` to it. Then, go to that folder. Example:

   ```bash
   $ cd $HOME
   $ mkdir gpt_13b_ss2k
   $ cp /projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss2k_run.sh gpt_13b_ss2k/
   $ cd gpt_13b_ss2k/
   ```

2. Open the `Gpt13b_ss2k_run.sh` file, and change `OUTDIR` to location of the run folder. Example:
   ```bash
   OUTDIR=${HOME}/gpt_13b_ss2k
   ```
   Note: the per device batch size is set to 32 here. Also, the number of steps is set to 10, but this can be changed. 

3. SambaNova uses SLURM for job submission and queueing. We will use sbatch to submit our job to the job scheduler. Please refer to [Sambanova Documentation](https://docs.alcf.anl.gov/ai-testbed/sambanova/job-queuing-and-submission/) for further details. In the following example, 4 RDUs are used:

   ```bash
   sbatch --output=log_gpt13b_ss2k_run.out --ntasks 4 --ntasks-per-node 4 --nodes 1 --gres=rdu:1 --cpus-per-task=32 Gpt13b_ss2k_run.sh
   ```

4. You can follow the status of your job using: `squeue`. The job should take about 8 min to complete.

5. Once the job is completed, you can see the accuracy metrics and checkpoint(s) (if enabled) in `hf_output_ss2k_run/`. The throughput is outputted toward the end of the log file.

   <details>
    <summary>Click for sample throughput (in the log file) </summary>

   ```bash
   {'e2e_train_time': 262.1321773529053, 'e2e_training_tokens_per_second': 10000.451018536301, 'training_tokens_per_second(exclude warmup overhead)': 10052.111972340099, 'final_loss': 9.262810707092285}
    ```

    </details>

    <details>
    <summary>Click for sample train_steps.txt</summary>

    ```bash
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    ```

    </details>

   <details>
    <summary>Click for sample train_loss.txt</summary>

    ```bash
   11.62805
   10.81699
   10.12060
   9.91110
   9.92652
   9.87338
   9.54991
   9.52660
   9.31008
   9.31859
    ```

    </details>

# Example 2 - Steps to run GPT 13B SS8k on SambaNova DataScale SN30 using 8 RDUs

**Note**: similarly here, we have precompiled the model and lowered the batch size and number of train steps to reduce the execution time.

1. Create a folder in your home repo, and copy the bash script `/projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss8k_run.sh` to it. Then, go to that folder. Example:
   
   ```bash
   $ cd $HOME
   $ mkdir gpt_13b_ss8k
   $ cp /projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss8k_run.sh gpt_13b_ss8k/
   $ cd gpt_13b_ss8k/
   ```

2. Open the `Gpt13b_ss8k_run.sh` file, and change `OUTDIR` to location of the run folder. Example:
   ```bash
   OUTDIR=${HOME}/gpt_13b_ss8k
   ```
   Note: here, the per device effective batch size is set to 32 and the grad accumulation steps to 4. Also, the number of train steps is set to 10, but this can be changed. 

2. Submit your job. In the following example, 8 RDUs are used:
   ```bash
   sbatch --output=log_gpt13b_ss8k_run.out --ntasks 8 --ntasks-per-node 8 --nodes 1 --gres=rdu:1 --cpus-per-task=16 Gpt13b_ss8k_run.sh
   ```

4. You can follow the status of your job using: `squeue`. The job should take about 42 min to complete.

5. Once the job is completed, you can see the accuracy metrics and checkpoint(s) (if enabled) in `hf_output_ss8k_run/`. The throughput is outputted toward the end of the log file.

   <details>
    <summary>Click for sample throughput (in the log file) </summary>

   ```bash
   {'e2e_train_time': 2103.653220653534, 'e2e_training_tokens_per_second': 9969.095568653116, 'training_tokens_per_second(exclude warmup overhead)': 9987.196849027754, 'final_loss': 9.63991928100586}
    ```

    </details>

    <details>
    <summary>Click for sample train_steps.txt</summary>

    ```bash
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    ```

    </details>

   <details>
    <summary>Click for sample train_loss.txt</summary>

    ```bash
    11.68751
    11.00089
    10.47739
    10.13234
    10.24533
    9.89494
    9.91220
    9.84972
    9.70797
    9.60735
    ```

    </details>


# Additional Resources

## Run Other Examples 

* See [Example Programs](https://docs.alcf.anl.gov/ai-testbed/sambanova/example-programs/) for instructions to run other well-known AI applications on SambaNova hardware (e.g., LeNet, MNIST, logistic regression, UNet2D, and GPT 1.5B)

## Useful Directories and Documentation

* [ALCF Sambanova Documentation](https://docs.alcf.anl.gov/ai-testbed/sambanova/getting-started/)
* [Sambanova Documentation](https://docs.sambanova.ai/developer/latest/sambaflow-intro.html) 
* Sambanova applications path: `/opt/sambaflow/apps/`
* Sambanova model scripts: `/data/ANL/scripts/`
* Important datasets: `/software/sambanova/dataset/`
