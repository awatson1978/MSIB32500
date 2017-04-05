
# Using a High Performance Computing cluster for bioinformatics analysis 

**Center for Research Informatics, University of Chicago**

April - June 2017; Saturdays 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.


## Learning Objectives

- Learn how develop HPC batch scripts using the Linux shell to execute code and develop analysis pipelines to perform computationally expensive bioinformatics tasks

## 1. Introduction

In this hand-on tutorial, you will learn how to use CRI's High Performance Computing (HPC) cluster TARBELL to perfom basic Bioinformatics analysis. TARBELL is a cluster with 2640 cores running **Scientific Linux 6** Update 4 with 2.6.32-358.18.1.el6.x86_64 kernel.  CRI also provides 1.3-petabyte storage space to be provisioned as **lab-shares** for BSD researchers. 

In this tutorial you will learn how to **access TARBELL cluster**, **transfer files**, create simple **PBS** job submission scripts and submit jobs in four hand-on exercises. Upon finishing the hand-on practices you will be able to use TARBELL cluster to perform simple quality control and sequence alignment analysis on Next Generation Sequencing (NGS) data.

**Prerequisites**

We will use SSH (Secure Shell) to connect to CRI's HPC. SSH is included in all standard Linux and Mac Operating Systems. If you are using MacOS or LinuxOS you can open the **Terminal** application.  If you are using Microsoft Windows, you'll have to install a SSH client on your computer. 

:pushpin:**Microsoft Windows user** you will need to install a tool for remote computing: [MobaXterm](http://mobaxterm.mobatek.net) and/or
[PuTTY](http://www.putty.org). PuTTY user go to: http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html locate the apropiate binary file (executable putty.exe file) for your hardware (32bits or 64 bits laptop). Place this file on your destop (or other folder that you can access easyly). You will need to 'double-click' this file each time you need to access it.

Open a PuTTY session, on 'Host Name (or IP address)' type: **tarbell.cri.uchicago.edu**,  select SSH as the Connection Type, verify the port number in the'Port' Box is **22**. Press the 'Open' button, then type in the provided **username and password** when prompted. Type **yes** if you are prompted to accept a key before entering username.


## 2. Login

For MacOS or Unix/Linux users:
1. Open a terminal session.
2. Connect to the login node of TARBELL cluster:

```bash
$ssh username@tarbell.cri.uchicago.edu
```
**CRI's TARBELL HPC diagram**

![tarbell](https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/cheatsheets/tarbell.jpeg)

By default, you will be logged into to the 'log-in' nodes **(in01 or in02)**, from there you will have access to the **storage/labshares** and **scratch** spaces (1Gb and 56 Gb speeds respectively). The log-in node also have access to the **scheduler and RM** nodes, the scheduler is the interface, to the **compute nodes (cn1, cn2, .. cn500)**. The log-in nodes also have access to the **cri-syncmon** node which is a dedicated Input gate node with several protocols/ports for data transfer enabeled.


Create a working directory and four sub-directories under your **home** directory for this had-on tutorial:

```bash
$ mkdir ~/mscbmi
$ cd mscbmi
$ mkdir Ex1 Ex2 Ex3 Ex4
```
## 3. Transfering data files

You can transfer files from your local computer to your home directory on the cluster or download the files from public databases and repositories. 

To download data from a website directly to your **working directory** on TARBELL cluster, you can use either the command **wget** or **curl** 

**Exercise 1.1:** Download a microarray expression raw data file from NCBI's Gene Expression Omnibus (GEO) (http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE31736) to your home directory on TARBELL cluster.

```bash
$ cd Ex1
$ wget 'http://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE31736&format=file' -O GSE31736_RAW.tar
$ ls  
$ rm GSE31736_RAW.tar
```

or
```bash
$ curl 'http://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE31736&format=file' -o GSE31736_RAW.tar
$ ls
$ rm GSE31736_RAW.tar
```
The '-o' option redirect the content to a file, otherwise it will appear on stdout, i.e. the screen.

To **upload the files from your local computer to TARBELL cluster**, you can use **scp or rsync** commands on Mac/Unix/Linux or Winscp on Windows.

**Exercise 1.2: ** Upload a file from your laptop/computer to your home directory on TARBELL cluster:

First, download the file available at the following link, to your local computer:

https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/data/GSE31736_RAW.tar 

Using computer command line (open a new terminal), navigate (use the cd command) to the directory where file 'GSE31736_RAW.tar' is located.

For Mac/Unix/Linux users:

To upload files from your local computer using **scp** use the following command:

```bash
scp PATH_TO_GSE31736_RAW.tar username@tarbell.cri.uchicago.edu:~/mscbmi/Ex1
```
Your command should look like: 

```bash
scp ./GSE31736_RAW.tar jandrade@tarbell.cri.uchicago.edu:~/mscbmi/Ex1
```
To upload files from your local computer using **rsync** use the following command:

```bash
rsync -avz GSE31736_RAW.tar username@tarbell.cri.uchicago.edu:~/mscbmi/Ex1
```
Windows users can also use GUI tools like WinSCP (http://winscp.net/download/winscp514setup.exe) to transfer files.


## 4. Running jobs on TARBELL HPC cluster

**Note: DO NOT RUN JOBS on the login nodes of the cluster. Always submit jobs to the compute nodes (qsub), or use the interactive mode (qsub -I)**

In this section, you will learn how to execute jobs on CRI's TARBELL cluster. We will use a tool for raw data quality control of NGS data as an example. The tool we will be using is a Java based program called [FastQC](http://www.bioinformatics.babraham.ac.uk/projects/fastqc/) 
This tool provides a modular set of QC analyses that can help you to evaluate the quality of your sequences, this is in general the first step on any NGS analysis pipeline.  

TARBELL cluster uses **Torque** as a resource manager (Provides low-level functionality to start, hold, cancel and monitor jobs) and **Moab** as Work-load Manager (job scheduler) to manage the cluster resources. Torque/Moab is based on the **Portable Batch System (PBS)** originally developed by NASA in the early 1990s. As such, **Torque/Moab uses PBS directives (commands)** to receive job requests from users.

 **What does a PBS script look like?**
 
![PBS](https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/cheatsheets/PBS.jpeg)

Torque provides user commands such as **qsub, qdel, qstat, etc.,** which are used to submit, delete and check the status of jobs on the cluster. TARBELL cluster supports two types of job submission:  and **batch mode** 

- Interactive mode (qsub -I): You will execute your code/commands in an 'interactive' command line window, you will be able to see the result/output of each action interactively, this mode is useful for testing and 'debugging' code.

- Batch mode: In a batch mode you first write a PBS script with all the instructions/code you want to execute, and then you submit that script to the scheduler. The batch job script contains all the information needed, such as the location of the input and output files, as well as run parameters. Once the batch job starts, you can log off and the job will remain running. 

** Exercise 2. Running job in interactive mode**

In this exercise, you will conduct the quality control analysis on a "good" quality sequence file and on a "bad" quality sequence file using FastQC program. 

First you will need to download two raw sequence files to your **home** directory on TARBELL cluster. 

You can do so using the command **wget or curl**:

- seqGood.fastq (https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/data/seqGood.fastq) 
- seqBad.fastq (https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/data/seqBad.fastq) 

Your command should look like: 

```bash
cd ~/msbmi/Ex2
wget ftp://logia.cri.uchicago.edu/bioinformatics/MSIB32500/Lecture3/Ex2/seqGood.fastq
wget ftp://logia.cri.uchicago.edu/bioinformatics/MSIB32500/Lecture3/Ex2/seqBad.fastq
ls -l
```

Let us first have a look at the sequence read fastq file. The following commands show the first and last two reads, as well as the total number of reads in seqGood.fastq file.

```bash
head -8 seqGood.fastq
tail -8 seqGood.fastq
grep --count ^@ERR030881 seqGood.fastq
```
Since each read in a fastq file has 4 lines, to find out how many reads are there in the fastq file, you can also use the folloing command:

```bash
wc -l seqGood.fastq
```
And divide the result by 4.


To **launch an interactive session using one core, use the following command:

```bash
qsub -I

cd ~/mscbmi/Ex2
```
Now You can run FastQC by typing:

```bash
module load fastqc
fastqc seqGood.fastq
ls
```

This will generate a self-contained directory called **"seqGood_fastqc.html"** which contains an HTML formatted report that can be loaded into a browser and a compressed file with all the results named **"seqGood_fastqc.zip**

Lets use the scp command, to copy the result files from your working directory in TARBELL to your local computer, so that we can explore the results. Open a new command line on your local computer and then run the following commands (you will need to use your own username and password):

```bash
scp jandrade@tarbell.cri.uchicago.edu:/home/jandrade/mscbmi/Ex2/seqGood_fastqc.zip ./
scp jandrade@tarbell.cri.uchicago.edu:/home/jandrade/mscbmi/Ex2/seqGood_fastqc.html ./
```

Now, in your local computer, go to the folder were you just copied the files (in my case is ./ or my home) and open the **seqGood_fastqc.html** file to explore the FastQC results. You can also unzip the **seqGood_fastqc.zip** file and review the **summary.txt** file for a summary of **PASS** and **FAIL** tests.


Repeat the steps to run FastQC on the **seqBad.fastq** file and compare the QC reports with the previous results (note you are still in the **interactive** mode session).

```bash
cd ~/mscbmi/Ex2
fastqc seqBad.fastq
exit
```
Note that after FastQC on the **seqBad.fastq** file, we used the command: **exit** to exit the **interactive** mode session.

Open a new command line on your local computer and then run the following commands (you will need to use your own username and password):

```bash
scp jandrade@tarbell.cri.uchicago.edu:/home/jandrade/mscbmi/Ex2/seqBad_fastqc.zip ./
scp jandrade@tarbell.cri.uchicago.edu:/home/jandrade/mscbmi/Ex2/seqBad_fastqc.html ./
```
Let's compare the FastQC results from  **seqGood.fastq** with **seqBad.fastg**, we will take a look at the Per base quality test:

**seqGood.fastq**

![good](https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/cheatsheets/perBaseGood.png)

**seqBad.fastg**

![bad](https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/cheatsheets/perBaseBad.png)

Gardner -> Lmod
Tarbell -> modules

See which modules are available to be loaded:
module avail

Load packages:
module load <package1> <package1>

module list

psub
qdel
qstat
qstat -f extended job status

qsub -I interactive

#PBS -s 

watch qstat
