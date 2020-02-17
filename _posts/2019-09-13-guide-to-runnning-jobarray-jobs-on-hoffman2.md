---
layout: post
title: Guide to running jobarray jobs on Hoffman2
description: 
publish: true
categories: 
- research
---

# Guide to running MATLAB jobarray jobs on Hoffman2

1. Log onto Hoffman2 using terminal using ssh `*user_name*@hoffman2.idre.ucla.edu` or using [NoMachine](https://www.hoffman2.idre.ucla.edu/access/nx/).

2. Request compute node: `qrsh -l h_rt=8:00:00,h_data=32G,highmem,highp` (see this [Using Hoffman2 Cluster](https://idre.ucla.edu/wp-content/uploads/2015/11/h2_20151005.pdf?a2f05c) guide for details on the explanation of optional parameters). If you want to request group-specific Nvidia GPU nodes (e.g. P4 or K40), simply append them to the end of the request command (e.g. ...highmem,highp,K40).

3. Navigate to the directory containing the MATLAB script you want to compile and run, then compile your MATLAB scripts using the mcc MATLAB compiler, `mcc -m file-name.m -I ~/path/to/directories/containing/dependencies -I ~/path/to/other/dependencies`. This will compile a MATLAB executable **file-name** (without .m extension) that can run independent of MATLB on compute cluster.

4. Generate a MATLAB command (.cmd) script for submitting a job to run the executable on remote compute node: `matexe.q -ns -o ~/job-output file-name`. This will generate a **file-name.cmd**. Note: Do not include the .m extension when performing matexe.q.

5. If you are NOT running a jobarray and only want to execute your MATLAB script as is, then you can use a text editor of your choice (e.g. emac, vim) to edit **file-name.cmd** (the `-l ...` line) to specify resource requests and then submit the command file to queue (see below). If you want to run a jobarray, then you also need to specify the parameter to submit with each job. A sample command file for **sampleScript.m** is shown below:
```
#!/bin/csh -f
#  sampleScript.cmd
#
#  UGE job for sampleScript built Wed Aug  7 22:30:05 PDT 2019
#
#  The following items pertain to this script
#  Use current working directory
#$ -cwd
#  input           = /dev/null
#  output          = /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID
#$ -o /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID
#  error           = Merged with joblog
#$ -j y
#  The following items pertain to the user program
#  user program    = /u/project/miao/y1lo/fib_genfire/scripts/sampleScript
#  arguments       = 
#  program input   = Specified by user program
#  program output  = Specified by user program
#  Resources requested
#
#$ -l h_data=16G,h_rt=2:00:00
#$ -t 1-121:1
#
# #
#  Name of application for log
#$ -v QQAPP=job
#  Email address to notify
#$ -M y1lo@mail
#$ -m bea
#  Job is not rerunable
#$ -r n
#
# Initialization for serial execution
#  
  unalias *
  set PROJECT_NAME="sAETGDFNarray70Tilt65Deg/"
  set qqversion = 
  set qqapp     = "job serial"
  set qqmtasks  = 8
  set qqidir    = /u/project/miao/y1lo/fib_genfire/scripts
  set qqjob     = sampleScript
  set qqodir    = /u/home/y/y1lo/job-output
  cd     /u/project/miao/y1lo/fib_genfire/scripts
  source /u/local/bin/qq.sge/qr.runtime
  if ($status != 0) exit (1)
#
  echo "UGE job for sampleScript built Wed Aug  7 22:30:05 PDT 2019"
  echo ""
  echo "  sampleScript directory:"
  echo "    "/u/project/miao/y1lo/fib_genfire/scripts
  echo "  Submitted to UGE:"
  echo "    "$qqsubmit
  echo "  SCRATCH directory:"
  echo "    "$qqscratch
#
  echo ""
  echo "sampleScript started on:   "` hostname -s `
  echo "sampleScript started at:   "` date `
  echo ""
#
  source /u/local/Modules/default/init/modules.csh
  module load matlab
  setenv MCR_CACHE_ROOT $TMPDIR
#
# Run the user program
#
  echo sampleScript "" \>\& sampleScript.output.$JOB_ID
  echo ""
  time /u/project/miao/y1lo/fib_genfire/scripts/sampleScript $SGE_TASK_ID $PROJECT_NAME >& /u/home/y/y1lo/job-output/sampleScript.output.$JOB_ID
#
  echo ""
  echo "sampleScript finished at:  "` date `
#
# Cleanup after serial execution
#
  source /u/local/bin/qq.sge/qr.runtime
#
  echo "-------- /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID --------" >> /u/local/apps/queue.logs/job.log.serial
 if (`wc -l /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID  | awk '{print $1}'` >= 1000) then
        head -50 /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID >> /u/local/apps/queue.logs/job.log.serial
        echo " "  >> /u/local/apps/queue.logs/job.log.serial
        tail -10 /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID >> /u/local/apps/queue.logs/job.log.serial
  else
        cat /u/home/y/y1lo/job-output/sampleScript.joblog.$JOB_ID >> /u/local/apps/queue.logs/job.log.serial
  endif
  exit (0)

```
Specifically, the lines to edit/add are 
```
#$ -l h_data=16G,h_rt=2:00:00
#$ -t 1-121:1
```
The option `-l ...` is for requesting the amount of resources for each compute node, much the same way you request a compute node when you first log onto Hoffman2. The option `-t 1-121:1` means each copy of your MATLAB executable that is running in a remote compute node will receive an input value (in type string) ranging from 1 to 121 in increments of 1 (there will be a total of 121 jobs). After you have defined the range of input variables, you need to somehow give this to the executable. This is achieved in line
```
time /u/project/miao/y1lo/fib_genfire/scripts/sampleScript $SGE_TASK_ID $PROJECT_NAME >& /u/home/y/y1lo/job-output/
```
by adding the `$SGE_TASK_ID` variable after the call to the executable. FYI, you can specify additional variables if your function takes in multiple variables. Here `$PROJECT_NAME` is another variable for sampleScript.m.

6. Submit the edited command file **file-name.cmd** to Hoffman2 job scheduler queue to run: `qsub file-name.cmd`.

7. You can monitor the status of your jobs by running `watch myjob`. This will continuously monitor the job queue. When the jobs are first submitted, they are in queue waiting (qw). If you request light resources, the jobs should run soon (<1 min) after submission (qw to r). If your jobs terminate right after running then there's probably a bug in the code somewhere. You can get more information by checking the job output, stored in ~/job-output/file-name.output.job_id.