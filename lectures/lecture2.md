
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

![Moore's law]( https://ourworldindata.org/wp-content/uploads/2013/05/Transistor-Count-over-time.png)


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
- TFLOPS: A TeraFlops is a trillion FLOPS one trillion floating-point operations per second
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



