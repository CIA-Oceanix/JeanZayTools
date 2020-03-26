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

