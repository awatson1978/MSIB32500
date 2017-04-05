
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

By default, you will be logged into to the log-in' nodes **(in01 or in02)**, from there you will have access to the **storage** and ** scratch** spaces (1Gb and 56 Gb speeds respectibly). The log-in node also have access to the **schedulell and RM** nodes, the scheduler is the interface, to the **compute nodes (cn1, cn2, .. cn500)**. The log-in nodes also have access to the **cri-syncmon** node which is a dedicated I/O node with several protocols/ports for data I/O enabeled.


Create a working directory and four sub-directories under your **home** directory for this had-on tutorial:

```bash
$ mkdir ~/mscbmil3
$ cd mscbmil3
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

**Exercise 1.2:** Upload a file from your laptop/computer to your home directory on TARBELL cluster:

First, download the file available at the following link, to your local computer:

https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/data/GSE31736_RAW.tar 

Using computer command line (open a new terminal), navigate (use the cd command) to the directory where file 'GSE31736_RAW.tar' is located.

For Mac/Unix/Linux users:

To upload files from your local computer using **scp** use the following command:

```bash
scp PATH_TO_GSE31736_RAW.tar username@tarbell.cri.uchicago.edu:~/mscbmil3/Ex1
```
Your command should look like: 

```bash
$ scp ./GSE31736_RAW.tar jandrade@tarbell.cri.uchicago.edu:~/mscbmil3/Ex1
```
To upload files from your local computer using **rsync** use the following command:

```bash
rsync -avz GSE31736_RAW.tar username@tarbell.cri.uchicago.edu:~/mscbmil3/Ex1
```
Windows users can also use GUI tools like WinSCP (http://winscp.net/download/winscp514setup.exe) to transfer files.


## 4. Running jobs on TARBELL HPC cluster

**Note: DO NOT RUN JOBS ON THE login nodes of the cluster!!! Always submit jobs to the computation nodes.**

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
