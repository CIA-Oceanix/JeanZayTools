# JeanZayTools

### Content:
Information and Sample code for using Jean ZAY supercomputer through Melody resource allocation

### Online tutorials: http://www.idris.fr/jean-zay/

### Login to JeanZay from IMT Atlantique
0. Filling and submitting registration forms for JeanZay (contact ronan.fablet@imt-atlantique.fr)
1. Connection to IMT Atlantique ssh server: ssh ssh.telecom-bretagne.eu
2. Connection to JeanZay using JeanZay login: ssh my_login@jean-zay.idris.fr

### Using Jupyter Notebooks on JeanZay
See http://www.idris.fr/jean-zay/pre-post/jean-zay-jupyter-notebook.html

### Considered/tested DL environments
- pytorch-gpu/py3/1.4.0, including pytorch and scikit-learn (contact: ronan.fablet@imt-atlantique.fr)

### Interactive execution mode 
- See http://www.idris.fr/jean-zay/gpu/jean-zay-gpu-exec_interactif.html
- An example below for the execution on a single GPU
1. module load pytorch-gpu/py3/1.4.0 (see above for the environment to be loaded)
2. salloc --ntasks=1 -A yrf@gpu --cpus-per-task=10 --gres=gpu:1 --hint=nomultithread --partition=gpu_p1
3. conda activate pytorch-gpu-1.4.0
4. ./python my_main

### Batch mode
- See http://www.idris.fr/jean-zay/gpu/jean-zay-gpu-exec_mono_batch.html
- An example below, when using a submission script:
  * Write a a submission script, denoted here as mono_gpu.slurm:
  ```
  #!/bin/bash
  #SBATCH -A yrf@gpu                  # account name
  #SBATCH --job-name=gpu_mono         # job name
  #SBATCH --ntasks=1                  # number of tasks (a unique process here)
  #SBATCH --gres=gpu:1                # number of gpu (a unique GPU here)
  #SBATCH --cpus-per-task=40          # number fo cores (1/4 of the node)
  #SBATCH --partition=gpu_p1          # change partition (preprost: test; gpu_p1: runs)
  #SBATCH --hint=nomultithread        # physical cores here (not logical)
  #SBATCH --time=04:00:00             # execution time required (HH:MM:SS)
  #SBATCH --output=gpu_mono%j.out     # output file
  #SBATCH --error=gpu_mono%j.err      # error file

  # cleaning the modules
  module purge
  # loading some modules
  module load geos/3.7.3
  module load tensorflow-gpu/py3/1.14-openmpi
  # add required informations from your path
  export PYTHONPATH=${HOME}/DINAE:${PYTHONPATH}
  # run the python code launch.py with 3 input arguments
  python launch.py ${1} ${2} ${3}
  ```
  * Submit the script:
  ```
  sbatch mono_gpu.slurm arg1 arg2 arg3
  ```
  * Use this command line to monitor your job 
  ```
  squeue -u UserID
  ```
  * And this one to kill it, if you figure a problem/bug in your application:
  ```
  scancel JobID
  ```
