# Introduction to Unix/Linux: 

## Learning Objectives

- This training will teach you all you need to know to start using Linux, be it on the CRI’s High Performance Infrastructure (HPC), or on your own computer (even if you are already running Windows or Mac OS).
- After this training you will: 
  - Feel comfortable using Linux
  - Know how software works on Linux  and how to use it
  - Use bash to execute commands in Linux and know your way around the file system
  - Have an overview of Linux tools that are extremely useful for bioinformatics

## Log on to CRI's High Performance Computing (HPC) system

```bash
ssh username@tarbell.cri.uchicago.edu
```
Enter your **_password_** when prompted. Type yes if you are prompted to accept a key.

## How to get help

- Use the manual ($ man) command; to exit the manual type 'q'
- Ask for help ($ your_command --help)
- Use the comand apropos ($ apropos text)

```bash
man ls
```
```bash
mkdir --help
```
```bash
apropos secure copy
```

## Navigation
1. List files in your home directory
```bash
ls            ### List the files in your current directory
ls -a         ### List the files in your current directory; do not ignore entries starting with .
```
2. Change current directory to the root of the file system and explore the directory structure
```bash
cd /          ### / represents the root of the file system
ls -l         ### List files in long format
pwd           ### Show the current directory
cd /tmp       ### Change current directory to /tmp
pwd
ls -l
```
3. Change to parent directory; one 'step' UP on the file tree
```
cd ..        
pwd
ls -l
```
4. Go back to your home directory
```bash
cd ~
pwd
```


 
