# Introduction to Unix/Linux: 

## Learning Objectives

- This training will teach you all you need to know to start using Linux, be it on the CRI’s High Performance Infrastructure (HPC), or on your own computer (even if you are already running Windows or Mac OS).
- After this training you will: 
  - Feel comfortable using Linux
  - Know how software works on Linux  and how to use it
  - Use bash to execute commands in Linux and know your way around the file system
  - Have an overview of Linux tools that are extremely useful for bioinformatics





This description assumes that you already have a
[user account on midway](http://rcc.uchicago.edu/getting-started/request-account). If
you do not have a *midway* account, please ask the instructor for
access. If you plan to use a different computing resource (e.g.,
another compute cluster, your own laptop), the exact steps described
here, and in subsequent episodes, will be slightly different for you.

We will employ
[Pair Programming](http://dx.doi.org/10.1145/2492007.2492020) in this
workshop. Introduce yourself to your partner and decide between you
who will be the **driver** and who will be the **observer/navigator**.
(Of course, you may alternate these roles throughout the workshop.)

We will use the University of Chicago
[Google Docs](http://gdocs.uchicago.edu) to help make this workshop
more interactive, and encourage discussion. Open up the
[Workshop Google doc](http://tinyurl.com/h8y6p9p) in your Web browser,
and **introduce yourself**.

Log on to midway using ssh with X forwarding:

```bash
ssh -X username@midway.rcc.uchicago.edu
```

Request an **interactive session** using the reservation for this
workshop. To safeguard against losing your connection, I recommend
using **screen**, but this is optional.
