
# Introduction to Parallel and distributed computing

**Center for Research Informatics, University of Chicago**

April - June 2017; Saturdays 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.


## Learning Objectives

- Learn the basics of parallel and distributed computing environments.
- Get familiar with basic models for parallel computation, and design of parallel and distributed algorithms. 

## 1. Why Parallel Computing

Moore's law refers to an observation made by Intel co-founder Gordon Moore in 1965. He noticed that the number of transistors per square inch on integrated circuits had doubled every year since their invention. Moore's law predicts that this trend will continue into the foreseeable future ***the number of transistors per square inch has since doubled approximately every 18 months.***
The figure bellow shows the number of trasistors on integrated circuits chips from 1971 to 2016: 

![Moore's law](https://ourworldindata.org/wp-content/uploads/2013/05/Transistor-Count-over-time.png)


Note: Exponential growth, it is unlikely to continue indefinitely, some new studie are showing that physical limitations could be reached this year - **2017**

**Factors contributing to validate Moore's law:**

- Denser integrated circuits
- Improvements on circuits architecture 

**Measures of processor performance**

Instructions per second: 

- MIPS: A million instructions per second.
- GIPS: A billion instructions per second
- TIPS: A trillion instructions per second
- PIPS: A Peta (10^5) instructions per second

Floating-point operations per second:

- MFLOPS: A million floating-point operations per second (FLOPS)
- GFLOPS: A GigaFlop is a billion FLOPS.
- TFLOPS: A TeraFlops is a trillion FLOPS, one trillion floating-point operations per second
- PFLOPS: A Peta (10^5) floating-point operations per second

Obviously, **there is a limit to the speed of a single processor*** (the speed-of-light), however the need for **FLOPS** in science and engineering **continue to grow exponetially** (wheather forecast, astrophisics, Monte Carlo simulation of nuclear reactors, etc.)

The only alternative for **efficient** analysis of BIG DATA is paralellel and/or distributed computing.

**Biologist are now joining the bid data club**

Due to available high-throughput genomics technologies (NGS), in January this year, Illumina was the first companny to anounce that their technology will be capable of sequencing a human genome for $1000 (with their HiSeq X 10 technology, a lab would be capable of sequencing 18,000 human genomes per year. Breaking down the price of an individual genome). 

How much data is produced? takea look at the troughput of the latest Illumina sequencing platforms: 

https://www.illumina.com/systems/sequencing-platforms.html

**Two examples:**
- The European Bioinformatics Institute _(EBI)_ in the UK currently stores **20 petabytes of data** and back-ups about genes, proteins and small molecules. 
- The Genomics Data Commons initiative _(GDC)_ at the University of Chicago, **currently host 5.42 petabytes of data and 87.96 Terabytes of RAM).** See the GDC's infrastructure statistics at: (https://gdc-portal.nci.nih.gov)

## 2. Hardware Paradigms for Parallel Computation: 

**CPU Design: Multiple-Core Processor**

A **multi-core processor** is a single computing component with *two or more independent actual processing units* (called "cores"), which are units that read and execute program instructions.

Although multicore chips were designed for game playing, they are becomming more and more popular in scientific computing. Now days, dual–core, quad–core, or even sixteen–core chips are commun on modern computers. These chips attain more integrated speed with less heat and more energy efficiency than single–core.

As an example: The *Sparc64-IXfx chip* has 16 Sparc cores that run at 1.85GHz and delivers 236 GFLOPS of double-precision floating point operations. Bellow the real architectural design of the chip:

![Fujitsu's Sparc64-IXfx processor](https://regmedia.co.uk/2011/11/20/fujitsu_sparc64_ixfx_chip.jpg)

**High Performance Computing** 

High-performance computing (HPC) is the use of **parallel processing** for running advanced application programs efficiently, reliably and quickly. The term applies especially to systems that function **above a TFLOP** or 10^12 floating-point operations per second. The term HPC is not a synonym for supercomputing, technically a supercomputer is a system that performs at the currently highest operational rate of more than a PFLOPS (10^15 floating-point operations per second).


**GRID Computing**

**Cloud Computing**

Cloud Computing: Computing and software resources that are delivered on demand, as service.

MSIB32500/cheatsheets/Cloud.jpeg

Software as a Service (SaaS) applications are hosted by a vendor and made available to customers over the Internet
Platform as a Service (PaaS) is a way to rent hardware, operating systems, storage and network capacity (and all associated service) over the internet
Infrastructure as a Service (IaaS)  an organization outsources the equipment used to support operations, including storage, hardware, servers and networking components. The service provider owns the equipment and is responsible for housing, running and maintaining it. The client typically pays on a per-use basis

Advantages

Pay as you go: Can be less expensive compared to buying installing and maintaining your own 
Flexibility: Theoretical infinite scalability
Easy Access: Can be used from any computer or device with an Internet connection
Easy updates: Updates occur across the service

Disadvantages

Security Concerns
Terms of Service
Privacy Policies


## 3. Programming Paradigms for Parallel Computation: 

- Dive and conquer - Divide the computation

Using Grid technology for computationally intensive applied bioinformatics analyses

http://www.bioinfo.de/isb/2006060046/main.html

- Divide the data


- Access more memmory



Programing languages for Distributed Computing:

BigDataScript

Develop ONE data pipeline and run exactly the same script everywhere. No matter how big the computer. Created by: Pablo Cingolani > Director of IT and Bioinformatics at Kew Inc.
Your program runs on a 25,000 core cluster or a single CPU laptop










Homework: Read the Nature technology feature article **'Biology: The big challenges of big data'** available at: http://www.nature.com/nature/journal/v498/n7453/full/498255a.html and submit via e-mail a one page critical commentary.

