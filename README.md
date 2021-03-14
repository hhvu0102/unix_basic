## Bioinformatics and Computational Biology Programming Workshop 2021
# Basic UNIX Totorial

**Original material by [Shane Dooley](https://github.com/skDooley/shell_tutorial) and Dr. Geetu Tuteja.
Modified and compiled by Ha Vu (Tuteja Lab).**

### Outline
0. Some installations
1. Introduction to UNIX
2. Basic essential programs
3. Examining files on the command line
4. Bedtools

# Some installations
# Introduction to UNIX
### What is UNIX? **TODO: images to illustrate Shell**
- A common operating system.
- What is an operating system?
    - An operating system is the suite of programs that make the computer work.
- The UNIX operating system is made up of the kernel, the shell, and the programs.
    - The **kernel** is the hub of the operating system. It allocates time and memory to programs.
    - The **shell** is the interface between the user and a kernel. It is a **command line** interpreter.
    - Shell commands can be run in the **terminal**.
### UNIX based operating systems
#### Linux
- Operating system and bundled application programs.
- Derived from Unix.
- Linux is free (open source).
- Linux is stable.
- Linux systems are highly customizable.
- **Computing clusters are all linux based.**

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

# Accessing HPC class TODO: request HPC class, screenshots to illustrate

# Basic essential programs
The general structure of a command line:
`program argument1 argument2 ...`

For example:
    `echo hello world`
    
| Term | Definition | Example |
|:-:|:-:|:-:|
|  program | the name (case sensitive) of the program  | echo |
|  argument | additional information you give the program to get it to do what you want it to do.  | hello world |    


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

#### cd
- `cd` = change directory.
- Helps you navigate between different directories.

#### Root vs home; Relative vs. absolute path
- Root = the first or top-most directory in a hierarchy.
- `home` directory is under the root.
- Where you are in the directory tree is called your path.
- In a path name, different directories and file names are separated by a slash `/`. The root has no name, so it's only one slash `/`.
    - For example:
    ```
    cd /
    pwd
    ```
- A path is either relative or absolute:
    - An absolute path = the root element and the complete directory list. For example, `/home/hhvu/unix_basic` is an absolute path.
    - A relative path needs to be combined with another path in order to access a file. For example, `unix_basic/practice` is a relative path.
- The current directory is denoted by `.`.
- The parent directory is denoted by `..`.
    - When we do `cd ..`, this will put us one directory above where we were.

#### Creation/Destruction
#### Shortcuts, wild cards, and tab completion

# Examining files on the command line
#### clear
#### cat
#### less
#### head
#### tail
#### grep
#### sort
#### uniq
#### wc
#### Redirect data `>`
#### Append data `>>`
#### Pipe

# Bedtools

Now, copy and paste the command below to your terminal: 
`git clone https://github.com/skDooley/shell_tutorial.git #todo`

Here, `git` is the program, `clone` and `https://github.com/skDooley/shell_tutorial.git` are arguments.
