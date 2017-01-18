# Introduction to Unix/Linux: 

**Center for Research Informatics, University of Chicago**

March - May 2017; 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.
**Teaching Assistant:** Wenjun Kand Ms.C.

## Learning Objectives

- This training will teach you all you need to know to start using Linux, be it on the CRI’s High Performance Infrastructure (HPC), or on your own computer (even if you are already running Windows or Mac OS).
- After this training you will: 
  - Feel comfortable using Linux
  - Know how software works on Linux  and how to use it
  - Use bash to execute commands in Linux and know your way around the file system
  - Have an overview of Linux tools that are extremely useful for bioinformatics

## Log on to CRI's High Performance Computing (HPC) system

In MacOS open the Terminal
:pushpin: If you are using a Windows machine (other than Windows 10 Anniversary Edition), you need install [MobaXter](http://mobaxterm.mobatek.net/)

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
a. List files in your home directory
```bash
ls            ### List the files in your current directory
ls -a         ### List the files in your current directory; do not ignore entries starting with .
```
b. Change current directory to the root of the file system and explore the directory structure
```bash
cd /          ### / represents the root of the file system
ls -l         ### List files in long format
pwd           ### Show the current directory
cd /tmp       ### Change current directory to /tmp
pwd
ls -l
```
c. Change to parent directory; one 'step' UP on the file tree
```bash
cd ..        
pwd
ls -l
```
d. Go back to your home directory
```bash
cd ~
pwd
```
## Operations with directories and files 

a. Create a new directory
```bash
mkdir mydir  ### Make a new directory called 'mydir'
mkdir newfolder1
ls -l 
```
b. Create a new file in a directory
```bash
cd mydir
nano file1.txt          ### Use nano editor to create a new file, write some text and use Control-O to save and Control-X to exit.
pwd
ls -l
```
c. Copy files and directories 
```bash
cp file1.txt copy.txt
ls -l
more copy.txt         ### Quick look to the contents of the file copy.txt
man more              ### Review the manual of the comand more; type q to exit
cp ~/mydir/*.txt ~/newfolder1/          ### copy all .txt files from mydir to newfolder1 
cd ~/newfolder1/
ls -l                 ### List the files you just copied
cd ..                 ### Change to parent directory
pwd
mkdir newfolder2
cd newfolder2
cp ~/newfolder1/file1.txt .     ### Copy file1.txt on current (.) directory
ls -l
cd ~
pwd
```
d. Remove a file or directory

```bash
cd newfolder1        
ls -l
rm file1.txt          ### Remove file1.txt
ls -l
cd                    ### Back to your home directory (this is equivalent to cd ~)
```

```bash
rm -r mydir           ### You will delete the whole mydir folder and all files on it, there is no way to recover those files
```
e. Rename a file or folder

```bash
cd newfolder1
mv copy.txt newname.txt         
ls -l
cd                              
mv newfolder1 newnamefolder                ### Rename newfolder1 with newnamefolder
```
f. Move files from one folder to another

```bash
mv newfolder2/file1.txt newnamefolder
```
g. Compress files

```bash
cd /group/bioinformatics/shared/MSIB32500/Lecture1/linux
ls -l SRR*                     ### List all files that start with SRR
gzip SRR001655.fastq           ### Compress a file, this command should create a compressed file named SRR001655.fastq.gz
ls -l                        
gunzip SRR001655.fastq.gz      ### Decompress a file
ls -l
```

:bulb: Review the [LinuxReference.pdf]() file a compilation of most useful Linux comand for bioinformatics 




 
