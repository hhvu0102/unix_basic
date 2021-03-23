## Gen 349 - Week 12 - Programming for Biologists
# Basic UNIX Totorial

**Original material by [Shane Dooley](https://github.com/skDooley/shell_tutorial) and Dr. Geetu Tuteja.
Modified and compiled by Ha Vu (Tuteja Lab).**

### Outline
0. Some installations
1. Introduction to UNIX
2. Basic essential programs
3. Examining files on the command line
4. Conclusion

# Some installations
## Connect to VPN
## Make sure you have access to either Putty, Windows Powershell, or Terminal. If you don't, tell us!

# Introduction to UNIX
### What is UNIX?
- A common operating system.
- What is an operating system?
    - An operating system is the suite of programs that make the computer work.
- The UNIX operating system is made up of the kernel, the shell, and the programs.
    - The **kernel** is the hub of the operating system. It allocates time and memory to programs.
    - The **shell** is the interface between the user and a kernel. It is a **command line** interpreter.
    - Shell commands can be run in the **terminal**.
    
<img src="/images/SHELL.png" width="500" height="400"/>

### UNIX based operating systems

#### Linux
- Operating system and bundled application programs.
- Derived from Unix.
- Linux is free (open source).
- Linux is stable.
- Linux systems are highly customizable.
- **Computing clusters are all Linux based.**

#### MacOSX
- More user friendly for beginners.

### UNIX in Bioinformatics
UNIX is useful...
- when you are trying to open a large FASTQ file.
- when you are searching for specific information from a large number of files.
- when you want to rename a large number of files.
- when you want to combine a large number of files into one file.
- when you need to run a program that is not available on Galaxy, and can only run in a UNIX-based environment.
- when you want to automate repetitive tasks.

# Accessing HPC class and some notes
Now we will connect to the HPC class for today's tutorial.
If you are on Putty, put the information as in the picture here:
<img src="/images/hpc-class.PNG" width="330" height="350" />

If you are on MACS Terminal, or Windows Powershell, do this:
```
ssh <your-net-id>@hpc-class.its.iastate.edu
```

Then put in your Net ID password. However, the terminal won't show any character when you type in.

## If you have questions:
- Put them in the chat.
- Or note them down and ask us at the end of the lecture.

Now, copy and paste the command below to your terminal: 

    git clone --single-branch --branch Gen349 https://github.com/hhvu0102/unix_basic.git

### How to paste:
- If you are in MACS terminal: `Command + V`
- If you are in Putty: `Right click`

# Basic essential programs
The general structure of a command line:
    `program [-flags] argument1 argument2 ...`

- For example:
    `echo hello world`
    
| Term | Definition | Example |
|:-:|:-:|:-:|
|  program | the name (case sensitive) of the program  | echo |
|  argument | additional information you give the program to get it to do what you want it to do.  | hello world |    

- Flags = options to run the program. Flags start with a single dash `-` or two dashes `--`, and change the behaviour of a command.

#### Tips
- Attention to detail is important.
    - Capitalization matters.
    - Spaces matter.
    - Semi colon, commas matter.
- Don’t try to rush through everything.

#### pwd
- `pwd` = print working directory.
- Tells you where you are sitting in the directory tree.
- Whenever you start up a terminal, you will start in a special directory called the `home` directory. Every user has their own home directory where they have full access to do whatever they want.

#### ls
- `ls` = list the files in the current directory.
- Another option: add flags to `ls`.
    - For example: `ls -l` 
- To explore all options to run `ls`, type `man ls`.

#### cd
- `cd` = change directory.
- Helps you navigate between different directories.

#### Root vs home; Relative vs. absolute path
- Root = the first or top-most directory in a hierarchy. Sometimes you won't have full access in `root`, e.g., when you are on university's high performance clusters.
- `home` directory is under the root.
- Where you are in the directory tree is called your path.
- In a path name, different directories and file names are separated by a slash `/`. The root has no name, so it's only one slash `/`.
    - For example:
    ```
    cd /
    pwd
    ls #check what is in the root directory
    ```
- A path is either relative or absolute:
    - An absolute path = the root element and the complete directory list. For example, `/home/hhvu/unix_basic` is an absolute path.
    - A relative path needs to be combined with another path in order to access a file. For example, `unix_basic/practice` is a relative path.
- The current directory is denoted by `.`.
- The parent directory is denoted by `..`.
    - When we do `cd ..`, this will put us one directory above where we were.

#### Poll time!
1. There's a directory called `hearingData` under the directory `lecture`. How would do go to the directory?
2. Which files listed below are in the `hearingData` directory?
    <p> A. Data0355, Data0493, Data0235 </p>
    <p> B. Data0335, Data0492, Data0225 </p>


#### Creation/Destruction
| Command | Description |
|:-:|:-:|
|mkdir| makes a directory|
|rmdir| removes an empty directory|
|touch <nameOfFile>| creates an file|
|rm <nameOfFile> | removes a file|
|rm -r <directory> | removes an entire directory and all of its contents|
|cp <filename> <destination>| copy a file to a location|
|mv <filename> <destination>| moves a file to a location|
    
For example:
```
mkdir testdir
cd testdir
touch testfile.txt
ls
cd ../
rm testdir
```

You cannot `rm testdir` here. Why?

## `rm -r` HAS GIVEN ME NIGHTMARES. BE CAREFUL!

#### Shortcuts, wild cards, and tab completion
##### Tilde ~
- `~` = a shortcut for your home directory.
- For example:
    `ls ~`
   
##### Wild card
- The `*` character matches against any character.
- For example, the following command list all the files in our current directory that contain "md" at the end of the file names:
    `ls *md`
    
#### Short poll time!
1. Do this command: `ls ~/unix_basic/lecture/hearingData/*4*2*`. What do you observe from the patterns of the file names?


##### Tab Completion
- Navigate to the home directory. Typing out directory names can waste a lot of time. When you start typing out the name of a directory, then hit the tab key, the shell will try to fill in the rest of the directory name. For example, enter:

    `cd u<tab>`
    
- The shell will fill in the rest of the directory name for `unix_basic`. Now enter:

    `ls ~/unix_basic/lecture/Diverse<tab><tab>`
    
- When you hit the first tab, nothing happens. The reason is that there are multiple files in the `practice` directory which start with `Diverse`. Thus, the shell does not know which one to fill in. When you hit tab again, the shell will list the possible choices.
- Tab completion can also fill in the names of programs. For example, enter `e<tab><tab>`. You will see the name of every program that starts with an `e`. One of those is `echo`. If you enter `ec<tab>` you will see that tab completion works.

    
# Examining files on the command line
#### clear
Sometimes your terminal is filled with past commands/outputs, and you want to have a clean terminal to avoid confusion. Then, you can do:

    clear

or hit `Ctrl + l`.

You can still scroll up to see past commands/outputs.

#### Quick check:
If I want to go to the directory `lecture` but I don't know where I am now, what should I do?
Let's go to the directory `lecture`!

#### cat
- `cat` = concatenate.
- Displays contents of file on screen.
    - For example:

        `cat ~/unix_basic/Gen349/lecture/Diverse-test.txt`
        
    - This will display the entire file at once. So it will look overwhelming if you have a big file!
- If you put two file names, it will display the first file, followed by the 2nd file.

#### less
- `less` opens the file, and lets you navigate through it.
- Use "space" to go forward and hit the "b" key to go backwards.
- The "g" key goes to the beginning of the file and "G" (i.e., `shift + G`) goes to the end.
- Finally, hit `q` to quit.

#### head
- `head` writes the first ten lines of a file to the screen.
- To change the number of lines printed, type `head -n <number> <file name>`.
- Quick question, where is the file `DiverseCas9s.faa`?
- Let's try: `head -n 5 DiverseCas9s.faa`

#### tail
- `tail` writes the last ten lines of a file to the screen.
- To change the number of lines printed, type `tail -n <number> <file name>`.
    - For example, `tail -n 5 DiverseCas9s.faa`
    
#### grep
- `grep` can search files for specific words or patterns.
- For example:
    `grep "locus" DiverseCas9s.faa`
- To explore other options, `man grep` or `grep -h` or `grep --help`
    
#### sort
- `sort` provides different options to sort a file.
- For example, `sort DiverseCas9s-names.txt` will sort the file `DiverseCas9s-names.txt` alphabetically based on the first column.
- If your file has multiple columns, you can use `-k` and the column number to sort by another column than the first (default).
- For more options in `sort`, type `man sort` or `sort --help` (`-h` may not work in this case).

#### Short poll time!
1. Read through the `man` page of `sort`. If I want to sort something **numerically**, what `-flag` should I use?
    A. `-b`
    B. `-i`
    C. `-r`
    D. `-n`


#### uniq
- `uniq` can be used to identify lines that occur uniquely in a file (`-u`), lines that are duplicated in a file (`-d`), or to count the number of occurrences in a file (`-c`)
- Without any options, it is similar to `sort -u` (which only keeps unique entries).
- Files must be sorted before running this command.

#### cut
- `cut` can be used to print only selected columns from a file.
- Examples:
    - Print column 1 of `DiverseCas9s-names.txt`, do `cut -f 1 DiverseCas9s-names.txt`.
    - Print column 1 and 3 from `DiverseCas9s-names.txt`, do `cut -f 1,3 DiverseCas9s-names.txt` (no space between `1,` and `3`).
- To explore other options, do `cut --help`.


#### wc
- `wc` will print newline, word, and byte counts for each file.
- Do `man wc` to find out all options in `wc`.
- For example, if you want to count the number of lines in a file:

    `wc -l DiverseCas9s.faa`
    
#### Short poll time!
1. If I want to count the number of words in a file, what `-flag` should I use?
2. How many words are there in the file `~/unix_basic/lecture/hearingData/Data0526`?

#### Redirect data `>`
- The following command puts the output on the screen.

    `grep "gbkey=CDS" DiverseCas9s.faa`

- What if you want to store the output to another file?

    `grep "locus_tag=STER" DiverseCas9s.faa > Cas9sOutput.txt`

#### Append data `>>`
- What if you want to add the search results to your output file that already exists?

    `grep 'protein_id=YP' DiverseCas9s.faa >> Cas9sOutput.txt`

- If you only used the `>` the text that was already in the file would be overwritten.

#### Pipe `|`
- The `|` command (hit `Shift + \`) allows you to connect the output of one command to the next command.
- Save time and memory when programming!
- For example:
    `grep 'protein_id=YP' DiverseCas9s.faa | wc -l`

# Conclusion
- The ability to use and navigate with UNIX is essential.
- Our best friends: Google, `man`, or `<program name> --help`.

### Let's take 5-min break, and we will come back with the last section. Ask us questions if you have any!

# BEDtools

BEDtools is a software package that allows easy comparison of genomic data
- Tasks that can be carried out with BEDtools are very common in genomic analysis
- BEDtools is also available on Galaxy 
- You may find yourself in a situation where it is
easier to run BEDtools locally on your computer
- Can integrate with other UNIX utilities (like sort, awk, etc)
- Don’t need to upload, run and download from Galaxy
- May not need the computational power of the Galaxy server for basic (but common) analysis

### BEDTools documentation
[http://bedtools.readthedocs.io/en/latest/index.html](http://bedtools.readthedocs.io/en/latest/index.html)

### bedtools intersect
- First, do `module load bedtools2` (this command evokes the program `bedtools2` that has been installed on our cluster. Not all programs are pre-installed like this, but most of the popular ones are).
Let us know when you are able to finish `module load bedtools2`.

- `bedtools intersect` allows one to screen for overlaps between two sets of genomic features.
- Usage:
```
bedtools intersect [OPTIONS] -a <FILE> \
                             -b <FILE1, FILE2, ..., FILEN>
```
- If I want to explore `[OPTIONS]` of `bedtools intersect`, what `flag` should I use?
- For whatever file we put right after the flag `-a`, that file is called the A file in this tutorial.
- For whatever file we put right after the flag `-b`, that file is called the B file in this tutorial.

#### Default behavior:
By default, if an overlap is found, bedtools intersect reports the shared interval between the two overlapping features.

For example, `bedtools intersect -a file1.bed -b file2.bed`

What are A file and B file in this case?

<img src="/images/bedtools-default.PNG" />


#### -wa Reporting the original A feature
Instead, one can force bedtools intersect to report the original “A” feature when an overlap is found. As shown below, the entire “A” feature is reported, not just the portion that overlaps with the “B” feature.

<img src="/images/bedtools-wa.PNG" />

#### -wb Reporting the original B feature
Similarly, one can force bedtools intersect to report the original “B” feature when an overlap is found. If just -wb is used, the overlapping portion of A will be reported followed by the original “B”. 

<img src="/images/bedtools-wb.PNG" />

#### Both -wa and -wb
If both `-wa` and `-wb` are used, the originals of both “A” and “B” will be reported.

#### -v
Only report those entries in A that have no overlap in B.
```
bedtools intersect -v -a file1.bed -b file2.bed
```

#### -u
Write original A entry once if any overlaps found in B. In other words, just report the fact at least one overlap was found in B.

Try `bedtools intersect -wa -a file2.bed -b file1.bed` and `bedtools intersect -u -a file2.bed -b file1.bed`. What's the difference?
