---
layout: post
title: Getting started with Conda
description: Python environment management
categories: 
- python
---

For beginner programmers such as myself who don't want to get bogged down with setting up a proper programming environment, and instead want to focus on writing codes for data analysis, Conda is a great program to help you circumvent the hassle and do all the necessary installations for you. Here I'll show how to quickly set up a usable Python environment using conda, assuming that Conda is already installed on your system.

## What's Conda?
Conda is an open source package and environment management system that quickly installs, runs and updates packages and their dependencies. In other words, Conda allows you to to create separate environments containing files, packages and their dependencies that will not interact with other environments. To learn more about Conda and how to install it, visit Conda's <a href="https://conda.io/docs/index.html" target="_blank">website</a>. 

Conda directory contains two main categories, 

`/pkgs`, where the different Python modules are stored in their individual directories, and `/envs`, which are conda environments that you set up, and allow you to host different versions of Python and modules of your choice. You can switch between different environments by activating and deactivating them.

## Create/Remove conda environment
Once you have installed conda, you can create a new custom environment with which to host different packages by running:

	conda create --name [environment-name] python=3.6

`python=3.6` is an optional parameter. It allows you to specify which version of Python to use in the new environment. 

To remove an environment, run: 

	conda remove --name [environment-name] --all

To activate the environment you just created, run (for macOS and Linux): 

	source activate [environment-name]

Or if you choose to deactivate the environment and use another one, run:

	source deactivate [environment-name]

To check which environment you're currently using, run: 

	conda info --envs

or

	conda env list

The active one will have * next to it.

To see list of installed packages in the current environment: 

	conda list

## Download packages in environment
Within the active environment, you can download packages by running: 

	conda install [package-name]

and it will download your desired package, as well as all other package dependencies of that package (this will save you a lot of work!). Let's say you want to install TensorFlow library, you can simply run: 

	conda install -c conda-forge tensorflow

and conda will ask you for permission to install the latest version of tensorflow and other packages, such as numpy, which tensorflow uses. The `-c` flag specifies the channel `conda-forge` to search for the `tensorflow` package. Note that in this case `conda-forge` is required because the latest version of this package (1.8.0) is not listed in the default channel that conda searches. 

To update packages/Python/conda:

	conda update [package-name]/Python/conda

I recommend reading through conda's <a href="https://conda.io/docs/user-guide/tasks/index.html" target="_blank">User Guide</a> for more usage details.

## Other tips
* You can export your active environment in the form of a `.yml` file:
		
		conda env export > [environment-name].yml

	This can be useful if someone else wants to use your environment on another computer to test your program. 


