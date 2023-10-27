# Sambanova

## Connection to Sambanova 

![Sambanova connection diagram](./sambanova_login.jpg)

Login to the Sambanova login node from your local machine.
Once you are on the login node, ssh to one of the sambanova nodes.

```bash
local > ssh ALCFUserID@sambanova.alcf.anl.gov
sm-login-1 > ssh sn30-r1-h1       
```

You can also ssh to `sn30-r1-h1 , sn30-r1-h2, sn30-r2-h1, sn30-r2-h2, sn30-r3-h1, sn30-r3-h2, sn30-r4-h1, sn30-r4-h2`

## Sambanova Examples

We use examples from Sambanova for this hands-on. 
Copy those examples to your home directory. 
```bash
cp -r /opt/sambaflow/apps/ ~
```

## Create Virtual Environment 

Sambanova software stack and associated environmental variables are setup at login. 

Each of the samples or application examples provided by SambaNova has its own pre-built virtual environment which can be readily used. They are present in the `/opt/sambaflow/apps/` directory tree within each of the applications. 

# Steps to run GPT13B on SambaNova DataScale SN30

**Note**: for the sake of the tutorial, we have precompiled the model and lowered the batch size and number of train steps to reduce the execution time.

1. Create a folder in your home repo, and copy the bash script `/projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss2k_GAS4_run.sh` to it. Then, go to that folder. Example:

   ```bash
   $ cd $HOME
   $ mkdir gpt_13b_ss2k
   $ cp /projects/aitestbed_training/SN/precompiled_gpt/bash_scripts/Gpt13b_ss2k_GAS4_run.sh gpt_13b_ss2k/
   $ cd gpt_13b_ss2k/
   ```

2. Open the `Gpt13b_ss2k_GAS4_run.sh` file, and change `OUTDIR` to location of the run folder. Example:
   ```bash
   OUTDIR=${HOME}/gpt_13b_ss2k
   ```
   Note: the per device batch size is set to 32 here. Also, the number of steps is set to 10, but this can be changed. 

3. SambaNova uses SLURM for job submission and queueing. We will use sbatch to submit our job to the job scheduler. Please refer to [Sambanova Documentation](https://docs.alcf.anl.gov/ai-testbed/sambanova/job-queuing-and-submission/) for further details. In the following example, 4 RDUs are used:

   ```bash
   $ sbatch --output=log_gpt13b_run.out --ntasks 4 --ntasks-per-node 4 --nodes 1 --gres=rdu:1 --cpus-per-task=32 Gpt13b_ss2k_GAS4_run.sh
   ```

4. You can follow the status of your job using: `squeue`. The job should take about 7 min to complete.



## Run Examples 

* [Lenet](./lenet.md)
* [GPT](./gpt.md)

## Useful Directories 

* Sambanova Applications Path : `/opt/sambaflow/apps`
* Sambanova Model Scripts : `/data/ANL/scripts`
* Important Datasets  : `/software/sambanova/dataset`

# Useful Resources 

* [ALCF Sambanova Documentation](https://docs.alcf.anl.gov/ai-testbed/sambanova_gen2/getting-started/)
* [Sambanova Documentation](https://docs.sambanova.ai/developer/latest/sambaflow-intro.html) 
* Sambanova Applications Path: `/opt/sambaflow/apps/`
* Sambanova Model scripts: `/data/ANL/scripts/`
* Important Datasets: `/software/sambanova/dataset/`
