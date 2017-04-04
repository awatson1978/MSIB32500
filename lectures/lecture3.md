
# Using a High Performance Computing cluster for bioinformatics analysis 

**Center for Research Informatics, University of Chicago**

April - June 2017; Saturdays 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.


## Learning Objectives

- Learn how develop HPC batch scripts using the Linux shell to execute code and develop analysis pipelines to perform computationally expensive bioinformatics tasks

## 1 Introduction

The Center for Research Informatics (CRI) hosts a High Performance Computing (HPC) cluster named TARBELL with 2640 cores running Scientific Linux 6 Update 4 with 2.6.32-358.18.1.el6.x86_64 kernel. 

CRI also provides 1.3-petabyte storage space to be provisioned as **labshares** for BSD researchers and labs. The HPC cluster serves as a platform for researchers who intend to conduct data-intensive large-scale computation which is not available on desktop or single workstation. 

In this tutorial you will learn how to access TARBELL cluster, transfer files, create simple job submission script and submit jobs in four hand-on exercises. Upon finishing the hand-on practices you will get familiar with basic Linux commands and be able to use TARBELL cluster to perform simple quality control and sequence alignment analysis on Next Generation Sequencing (NGS) data.

Prerequisites
We will use SSH (Secure Shell) to connect to CRI's HPC. SSH is included in all standard Linux and Mac Operating Systems, but it is not included in Windows Operating System. If you are using Windows, you'll have to install a SSH client on your computer. It is strongly recommended that you use PuTTY SSH for Windows-based systems. You can download Putty from http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html and double click putty.exe to install it.
Login
The login procedure varies slightly depending on whether you use a Windows computer or Mac/Unix/Linux computer.
For Mac or Unix/Linux users:
1. Open a terminal session.
2. Connect to the login node of TARBELL cluster:

```bash
$ssh username@tarbell.cri.uchicago.edu
```


