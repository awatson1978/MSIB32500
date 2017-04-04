
# Using a High Performance Computing cluster for bioinformatics analysis 

**Center for Research Informatics, University of Chicago**

April - June 2017; Saturdays 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.


## Learning Objectives

- Learn how develop HPC batch scripts using the Linux shell to execute code and develop analysis pipelines to perform computationally expensive bioinformatics tasks

## 1 Introduction

In this hand-on tutorial, you will learn how to use CRI's High Performance Computing (HPC) cluster TARBELL to perfom basic Bioinformatics analysis. TARBELL is a cluster with 2640 cores running **Scientific Linux 6** Update 4 with 2.6.32-358.18.1.el6.x86_64 kernel.  CRI also provides 1.3-petabyte storage space to be provisioned as **lab-shares** for BSD researchers. 

In this tutorial you will learn how to access TARBELL cluster, transfer files, create simple **PBS** job submission scripts and submit jobs in four hand-on exercises. Upon finishing the hand-on practices you will be able to use TARBELL cluster to perform simple quality control and sequence alignment analysis on Next Generation Sequencing (NGS) data.

**Prerequisites**

We will use SSH (Secure Shell) to connect to CRI's HPC. SSH is included in all standard Linux and Mac Operating Systems. If you are using MacOS or LinuxOS you can open the **Terminal** application.  If you are using Microsoft Windows, you'll have to install a SSH client on your computer. 

```
Microsoft Windows user you will need to install a tool for remote computing: [MobaXterm](http://mobaxterm.mobatek.net) and/or PuTTY (http://www.putty.org)
Please go to: http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html locate the apropiate binary file (executable putty.exe file) for your hardware 32bits or 64 bits laptop. Place this file on your destop (or other folder that you can access easyly). You will need to 'doble-click' the putty.exe file everytime that you need to access it.
```


It is strongly recommended that you use PuTTY SSH for Windows-based systems. You can download Putty from http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html and double click putty.exe to install it.
Login
The login procedure varies slightly depending on whether you use a Windows computer or Mac/Unix/Linux computer.
For Mac or Unix/Linux users:
1. Open a terminal session.
2. Connect to the login node of TARBELL cluster:

```bash
$ssh username@tarbell.cri.uchicago.edu
```


