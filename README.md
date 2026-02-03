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
---

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
#### 2. Streams and Redirection in Linux
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


Example:
```bash
echo "ATCG" > sequence.txt
cat sequence.txt >> all_sequences.txt
grep "geneX" file.gtf 2> error.log
```

#### 3. Introduction to grep
grep is used to search for patterns in files. This command is useful for finding motifs, genes, or sequence patterns.
-v : an invert matching flag used in grep to display lines that do not contain the specified pattern, instead of those that do. 
Example
```bash
grep "ATCG" sequence.txt
```

#### 4. Pipes (|)
Pipes connect the output of one command to the input of another.
Example:
```bash
grep -v "^>" tb1.fasta | grep --color"[^ATCG]" # -v: invert matching flag and '^' used to denote beginning of the line
```
^ inside [ ] = NOT

^ outside [ ] = start of line

---

## Class 3: File Viewing and grep
This class focused on viewing large biological files, extracting relevant information, and automating simple tasks using Linux commands and bash scripting. These commands are essential for exploring large genomic annotation files, counting sequences, filtering unwanted data, and automating repetitive analyses in bioinformatics workflows.

### Topics Covered

#### 1. Viewing File Contents
- `cat` – Displays the entire content of a file  
- `less` – Views large files page by page (useful for GTF/GFF files)

Example:
```bash
cat genes.txt
less annotation.gtf
```
#### 2. Viewing Specific Lines
- `head –` Displays the first few lines of a file (manually 10 lines)
- `tail` – Displays the last few lines of a file (manually 10 lines)
- `-n` – Specifies the number of lines

Example:
```bash
head -n 5 sample.fasta
tail -n 10 sample.fasta
(head -n 3; tail -n 3;) < filename.txt # '<' inspect the file
```

#### 3. Searching Using grep
- grep – Searches for a pattern in a file
- grep -o – Prints only the matched pattern
- grep -c – Counts the number of matching lines
- grep -v – Prints lines that do NOT match the pattern

Examples:
```bash
grep "gene_id" annotation.gtf
grep -o "gene_id \"[^\"]*\"" annotation.gtf
grep -c ">" tb1.fasta
grep -v ">" tb1.fasta
```

#### 4. Combining Commands with Pipes
Pipes (|) are used to pass output from one command to another.

Example:
```bash
grep -v ">" tb1.fasta | wc -l #This counts the number of sequence lines excluding FASTA headers.
grep -v ">" tb1.fasta | wc -m #This counts the number of characters
grep -v ">" tb1.fasta | wc -w #This counts the number of words
cat annotation.gtf | head

```
#### 5. Basic Bash Scripting
Bash scripting allows automation of repetitive tasks.

Example:
```bash
echo "There are $(grep -c ">" tb1.fasta) entries in my fasta file"
This command dynamically counts the number of sequences in a FASTA file and prints the result.
```
--- 

## Class 4: Git for Scientists

This class introduced Git as a version control system to track changes in code, scripts, and analysis files.
Git helps scientists:
- Track changes in analysis scripts
- Maintain reproducibility
- Collaborate efficiently
- Avoid accidental data loss
- Document the evolution of research workflows
It is widely used for managing bioinformatics pipelines, scripts, and documentation.


### 1. Configuring Git
Git configuration is done once to associate commits with a user.

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
ssh -keygen -t rsa -b 4096 -c "your_email@example.com" # ssh - secure shell protocol, configure our computer terminal comunication with website
```
#### 2. Creating and Initializing a Repository
A Git repository is used to track changes in a project directory.
`git init`
This initializes a local Git repository by creating a .git directory.

#### 3. Understanding the Working Tree
Git tracks files in three stages:
1. Working directory – files being edited 
2. Staging area – files marked for commit
3. Repository – committed snapshots
Commands used:
`git status`
`git add filename`
`git commit -m "Commit message"`
only after git add filename the file starts to be tracked else their status remain untracked files

#### 4. Tracking Changes
- `git status` – shows tracked and untracked files
- `git diff` – shows changes between versions
- `git log`– displays commit history

#### 6. Restoring and Removing Files
- `git restore filename` – discard local changes
- `git restore --staged filename` – unstage files
- `git rm filename.txt` – remove file from Git tracking
Example:
```bash
git restore --staged data.txt
git rm old_script.py
```

#### 7. Renaming and Ignoring Files
- `git mv create.txt create.py` - This tracks file renaming without losing history.
- Files that should not be tracked (e.g., temporary files, large outputs) are listed in .gitignore.
Example:
```bash
touch .gitignore
echo "*.log" >> .gitignore
cat .gitignore
git add .gitignore # if you want to commit the ignored files
```

#### 8. Connecting to a Remote Repository (GitHub)
A remote repository allows sharing and backing up code.
```bash
git remote add origin https://github.com/username/repository.git
git branch -M main
git push -u origin main
```

#### 9. Working with Remote Repositories
- `git pull` – fetch and merge changes from remote
- `git clone` – copy a remote repository locally
Example:
```bash
git pull origin main
git clone https://github.com/username/repository.git
```
---

## Class 5: Text Processing
These commands are used to summarize and analyze large datasets efficiently.The techniques learned in this class are essential for preprocessing genomic files, extracting biologically meaningful information, validating datasets, and building reproducible bioinformatics pipelines.
#### 1. Working with Specific Columns Using cut
The cut command extracts specific columns from tab-delimited files such as BED, GTF, or TSV files.

Example:
```bash
cut -f 2 filename.bed | cut -f 1,4,5 | head -n 3 > test.txt  # This extracts selected columns and saves the output to a new file.
```

#### 2. Advanced Searching Using grep
This finds all entries except those related to a specific gene.
- `grep "geneX" annotation.gtf` - Searching Randomly or Flexibly
- `grep -v "geneY" annotation.gtf` - Excluding Specific Patterns


#### 3. Highlighting Matches with Color
a. `grep --color=always "ATCG" sequence.fasta`
  - it always colour no matter what
  - works in redirected
  - this is better if you want to see less
  - Not recommended when saving output to a file, as color escape codes are included
Example:
```bash
grep --color=always "ATCG" sequence.fasta | less
```

b. `grep --color=auto "ATCG" sequence.fasta` 
  - highlight the matching pattern only when output goes to terminal
  - does nnot color piped or redirected output
  - Better when saving results to a file, as no color codes are written
Example:
```bash
grep --color=auto "ATCG" sequence.fasta > matches.txt
```

#### 4. Context Line Control in grep and Multiple Pattern Matching
Context options allow viewing surrounding lines of a match.
- `-A` – Lines after the match
- `-B` – Lines before the match
- `-C` – Lines before and after the match
- `-E` - searches for multiple pattern in a single command.
Example:
```bash
grep -C 2 "gene_id" annotation.gtf
grep -A 2 "gene_id" annotation.gtf
grep -B 2 "gene_id" annotation.gtf
grep -E (geneA|geneB) annotation.gtf # '|' is OR in this 
```

#### 5. Counting, Sorting, and Combining Results
- `grep -c` – Counts the number of lines that contain the pattern
- `grep -w` - Only whole word matches
- `grep -cw` - Counts whole-word lines
- `sort` – Sort results
- `uniq` – Filter unique entries
- `join` – Combine files based on a common field. Both files MUST be sorted on the join column
Example:
```bash
grep -cw "gene_id" annotation.gtf 
sort -k1,1 -k2,2n filename.bed # -k1 is first column , -k2 is 2nd column and 2n is numerical factor
sort letters.txt | uniq # always sort before filtering unique entries
join -1 1 -2 1 sorted.bed example_length.txt > join.bed 
```
- `-1 1` - Use column 1 of the first file (sorted.bed) as the join key
- `-2 1` - Use column 1 of the second file (example_length) as the join key

---

## Conclusion

All the classes were insightful and helped me understand the importance of Linux and GitHub in bioinformatics. Bioinformatics involves the analysis of large-scale sequencing data, and most bioinformatics tools and pipelines, such as QIIME,MAFT,BLAST,SAMtools/BCFtools,FastQC,VEP, are designed to run on Linux systems. Linux is faster, more efficient, and well suited for handling large datasets and command-line–based analyses.

GitHub is also an essential part of bioinformatics workflows, as it supports version control, reproducibility, and proper documentation of analyses. Sharing code and documentation through GitHub allows other bioinformaticians to understand, reproduce, and build upon existing work. Since bioinformatics often lacks sufficient documentation, using GitHub helps improve transparency and research quality.


