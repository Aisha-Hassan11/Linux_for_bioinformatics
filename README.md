# Linux and Git Learning Log

## Table of Contents
- [Introduction](#introduction)
- [Class 1: Linux Basics](#class-1-linux-basics)
- [Class 2: Streams and grep](#class-2-streams-and-grep)
- [Class 3: File Viewing and grep](#class-3-file-viewing-and-grep)
- [Class 4: Git for Scientists](#class-4-git-for-scientists)
- [Class 5: Text Processing](#class-5-text-processing)
- [Conclusion](#conclusion)

---

## Introduction
This repository documents what I learned in each class related to Linux command-line tools and Git version control, as part of my coursework. It contains the codes I learned in the classes. the purpose is to document it for future reference. This respository contains basic and  beginnner stuffs about linux and git to get started as bioinformatics or anyone who is interested in this.


---

## Class 1: Linux Basics
What is Linux?

Linux is an open-source operating system widely used for development and servers. 

How is it useful for bioinformatics?

Bioinformatics involves the analysis of large-scale sequencing data, often in gigabytes or terabytes. Linux is the preferred operating system for bioinformatics because it efficiently handles large datasets and provides powerful command-line tools for data preprocessing and downstream analysis. Many bioinformatics software tools and pipelines are developed for Linux, making it essential for managing, processing, and analyzing high-throughput sequencing data.

In this class i learned about the fundamentals of Linux command line.

### Topics covered
#### 1. Navigating the File System
Linux uses a hierarchical file system structure. Learning how to move through directories is crucial when working with large projects and datasets.

- `pwd` – Displays the current working directory  
- `cd` – Changes the directory  
- `/` – Represents the root directory and is used as a path separator

Example:
```bash
cd /home/user/project
pwd
```

#### 2. Listing files and directory 
This command helps in checking all the available files. 

- `ls` - Display all the files
- `ls -a` - Display hidden files
- `ls -l` - Displays detailed file information

#### 3. Creating files, directories and others
- `mkdir` - makes a directory
- `touch` - create empty files
- `echo` - Prints a message to the terminal or writes output to a file  
- `cat` - Display the content of  file
- `cp` - copy and paste
- `mv` - move files or rename the files
- `rm` - remove files
- `rm -r` – Removes directories recursively
- `rm -f` – Forces deletion without confirmation
- `clear` - clear the screen
- `history` - shows the history of command used in the terminal
- `man` - shows manual of the command you need to know
  Example:
```bash
mkdir demo
touch demo_2.tsv
echo "hello world" > demo_2.tsv
cat demo_2.tsv
cp demo/demo_2.tsv random.tsv # copy demo_2.tsv to random.tsv
cp demo/demo_2.tsv -t demo_2  # -t is a flag used for the directories
mv demo_2 test # rename the file from demo_2 to test
rmdir test_1  # remove empty directory
rm -rf demo_2.tsv # force remove the files, use this with caution
man cp # shows manual of cp 
```

## Class 2: Streams and grep
In this class we learned how to work with biological sequence files and use Linux commands to efficiently search, filter, and manipulate data.

#### 1. wildcards and creating fastq files
Wildcards allow working with multiple files at once or to find part of a phrase in a text file.

- `*` – Matches any number of characters  
- `?` – Matches a single character  
- `[ ]` – Matches one character from a specified set
Example:
```bash
touch sample{A,B,C}_R{1,2}.fastq
ls sample_*.fastq
ls sample?_r1.fastq
ls sample [A-C]_R1.fastq
```
#### 3. Streams and Redirection in Linux
Linux uses three standard streams:
stdin (0) – input
stdout (1) – output
stderr (2) – error
These streams allow flexible data flow between commands.

Redirection is used to send output to a file or take input from a file.
- `>` – Redirect output (overwrite)
- `>>` – Redirect output (append)
- `<` – Redirect input
- `2>` - Redirect standard error (overwrite)
- `2>>` - Redirect standard error (append)

#### 4. Streams and Redirection in Linux


## Class 3: File Viewing and grep
Write about `cat`, `less`, `head`, `tail`, and advanced grep.

---

## Class 4: Git for Scientists
Explain Git configuration and commands you learned.

---

## Class 5: Text Processing
Write about `cut`, `grep` with options, sorting, counting, etc.

---

## Conclusion
Summarize your learning journey.

