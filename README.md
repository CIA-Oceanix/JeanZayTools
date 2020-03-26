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
- xxxx (contact: xxxx)

### Interactive execution mode 
- See http://www.idris.fr/jean-zay/gpu/jean-zay-gpu-exec_interactif.html
- An example below for the execution on a single GPU
1. salloc --ntasks=1 -A yrf@gpu --cpus-per-task=10 --gres=gpu:1 --hint=nomultithread --partition=gpu_p1
2. module load xxx (see above for the environment to be loaded)
3. ./python main

### Interactive execution mode 


