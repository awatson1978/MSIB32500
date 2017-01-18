# Introduction to Unix/Linux: 

**Center for Research Informatics, University of Chicago**

April - June 2017; Saturdays 9:00AM - 12:00PM

**Instructor:** Jorge Andrade, Ph.D.

**Teaching Assistant:** Wenjun Kang, Ms.C.

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

:bulb: Download and Review the [LinuxReference.pdf](https://github.com/MScBiomedicalInformatics/MSIB32500/blob/master/cheatsheets/LinuxReference.pdf) file, a compilation of basic and most useful Linux comand for bioinformatics 

## File transfer between computers

a. Windows user download and install [WinSCP](http://winscp.net/eng/index.php). MacOS users open the Terminal
The *scp* (secure copy command) allows you to copy/move files between compters on the command line
```bash
scp example1.txt username@tarbell.cri.uchicago.edu:.
```
:bulb: The [hypexr.org](http://www.hypexr.org/linux_scp_help.php) website has nice list of examples on how to use secure copy (also some [computer comics and cartoons](http://www.hypexr.org/comics.php))

b. You can use *wget* to get a file from the internet directly to your working directory in Linux
```bash
wget http://downloads.yeastgenome.org/curation/chromosomal_feature/saccharomyces_cerevisiae.gff
```
## Input/Output redirect and pipe

a. Use the symbol '>' to redirect the output of a command to a file

```bash
nano text1.txt                       ### Create a new file and write some text on it
 
cat text1.txt                        ### Print file1.txt to screen
 
cat text1.txt > text2.txt            ### Print file1.txt to file2.txt
 
nano text2.txt                       ### Use nano to view file2.txt

```
b. Use the symbol '>>' to redirect the output of a command to a file using 'append'

```bash
cat file1.txt >> file2.txt           ### Append file1.txt to file2.txt
nano file2.txt                       ### View file2.txt
```
c. Use the symbol '<' to redirect the input
```bash
cat < file1.txt                      ### Print file1.txt to screen
```
d. Use the symbol '|' to pipe the output of one command as the input of another 

```bash
ls | wc -l              ### List the files and folders in the current directory and then count them
```
## Text extraction and manipulation

A standard Unix/Linux installation will have available several text editors (like: vi, vim, nano, emacs, and others) and text viewers (like: less, more, head and tail)

a. Use the symbol '>' to redirect the output of a command to a file

```bash
cd /group/bioinformatics/shared/MSIB32500/Lecture1/linux               
less SRR001655.fastq                 ### View a fastq file: use q to exit, space or f to the next page,
                                     ### b to the previous page, and / to search a word
head -20 SRR001655.fastq             ### Show the first 20 line of the file
tail -20 SRR001655.fastq             ### Show the last 20 lines of the file

```
b. Pattern Search with 'grep'. The grep command searches specified files or other input(stdin) for patterns matching a given expression(s).

```bash
> cat list1.txt                      ### See the contents of file list1.txt
apples
bananas
plums
carrots
 
> cat list2.txt                      ### See the contents of file list2.txt
Apple Sauce
wild rice
black beans
kidney beans
dry apples
 
> grep apple list1.txt list2.txt     ### Search for "apple" in list1.txt and list2.txt
list1.txt:apples
list2.txt:dry apples
```



