---
layout: post
title: Training neural networks on computing clusters
description:
publish: true
categories: 
- linux
---

Recently I've been trying to outsource my neural network training onto a computing cluster (the Hoffman2 cluster at UCLA). Specifically, I'm trying to use Tensorflow's implementation of the CNN model on CIFAR-10 dataset. Training the model interactively was not difficult. I just had to load the Anaconda module, install Tensorflow package and its associated modules, then train the model. However, to do it non-interactively, i.e. submit as a job to a remote node, it requires writing up a simple C shell script for submission. I'm posting the command file for job submission here for those who may be interested in implementing machine learning on a computing cluster.

This part gives the [Sun Grid Engine](https://en.wikipedia.org/wiki/Oracle_Grid_Engine) job scheduler some parameters for initiating a remote job, providing information on how much memory to request, how long to run the job for, etc. 
	
	#!/bin/csh -f
	#
	#$ -cwd
	#$ -o output/directory
	#$ -j y
	#$ -l exclusive,h_data=8G,h_rt=6:00:00
	#$ -v QQAPP=job
	#$ -M email_for_sending_job-related_notifications@email.com
	#$ -m bea
	# job is rerunable
	#$ -r n

Not sure what below lines do, but they apparently set the path to the files related to the training.

	 unalias * # Remove all previous aliases
	 
	 set qqversion =
	 set qqapp = "job serial"
	 set qqmtasks = 8
	 set qqidir = directory/to/training/files
	 set qqjob = file name
	 set qqodir = directory/to/training/files

Change to the project directory and initiate the job scheduler.

	 cd /path/to/project/directory
	 source /u/local/bin/qq.sge/qr.runtime
	 if ($status != 0) exit (1)

Load Anaconda and load Python environment.

	 echo "Load modules..."
	 source /u/local/Modules/default/init/modules.csh
	         module load anaconda/python3-4.2

Activate TensorFlow conda environment. One caveat here is that there is a conflict for the command `source` in both C shell and conda (normally you would activate Tensorflow with `source activate tensorflow`), so you cannot directly call `source` to activate the tensorflow environment inside your csh script. Fortunately, someone has written a csh version of the `activate` command that is available on [GitHub](https://gist.github.com/mikecharles/f09486e884a0b41e1e8f), so you can activate the tensorflow environment by directly calling it in the script.

	 echo "Anaconda loaded"
	 setenv CONDA_ENVS_PATH /path/to/conda/environments # Set path to search for Conda environments
	 source /path/to/activate.csh tensorflow # Use CSH version of conda activate to change to tensorflow environment
	 setenv PATH /path/to/tensorflow/conda/environment/bin:$PATH # Add Tensorflow env to beginning of search paths
	 echo "Tensorflow loaded"
	 setenv MCR_CACHE_ROOT $TMPDIR

Begin training the neural network! This also prints the output to a text file so you can check the progress as it goes along. Note that the output does not update instantaneously, so don't freak out if you don't see anything in the file right away.

	 echo "Begin model training..."
	 python cifar10_train.py | tee -a train_cifar10.output.$JOB_ID

	 source /u/local/bin/qq.sge/qr.runtime
	 exit(0)

Hope this helpes!


