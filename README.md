## Bioinformatics and Computational Biology Programming Workshop 2021
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

# Accessing HPC class TODO: request HPC class, screenshots to illustrate

Now, copy and paste the command below to your terminal: 

    git clone https://github.com/hhvu0102/unix_basic.git


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
- Root = the first or top-most directory in a hierarchy.
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

`rm -r` HAS GIVEN ME NIGHTMARES. BE CAREFUL!

#### Shortcuts, wild cards, and tab completion
##### Tilde ~
- `~` = a shortcut for your home directory.
- For example:
    `ls ~`
   
##### Wild card
- The `*` character matches against any character.
- For example, the following command list all the files in our current directory that contain "md" at the end of the file names:
    `ls *md`

##### Tab Completion
- Navigate to the home directory. Typing out directory names can waste a lot of time. When you start typing out the name of a directory, then hit the tab key, the shell will try to fill in the rest of the directory name. For example, enter:

    `cd u<tab>`
    
- The shell will fill in the rest of the directory name for `unix_basic`. Now enter:

    `ls ~/unix_basic/practice/Diverse<tab><tab>`
    
- When you hit the first tab, nothing happens. The reason is that there are multiple files in the `practice` directory which start with `Diverse`. Thus, the shell does not know which one to fill in. When you hit tab again, the shell will list the possible choices.
- Tab completion can also fill in the names of programs. For example, enter `e<tab><tab>`. You will see the name of every program that starts with an `e`. One of those is `echo`. If you enter `ec<tab>` you will see that tab completion works.

    
# Examining files on the command line
#### clear
Sometimes your terminal is filled with past commands/outputs, and you want to have a clean terminal to avoid confusion. Then, you can do:

    clear

or hit `Ctrl + l`.

You can still scroll up to see past commands/outputs.

#### cat
- `cat` = concatenate.
- Displays contents of file on screen.
    - For example:

        `cat ~/unix_basic/lecture/Diverse-test.txt`
        
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
    - For example, `head -n 5 DiverseCas9s.faa`

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

#### uniq
- `uniq` can be used to identify lines that occur uniquely in a file (`-u`), lines that are duplicated in a file (`-d`), or to count the number of occurrences in a file (`-c`)
- Without any options, it is similar to `sort -u` (which only keeps unique entries).
- Files must be sorted before running this command.

#### wc
- `wc` will print newline, word, and byte counts for each file.
- Do `man wc` to find out all options in `wc`.
- For example, if you want to count the number of lines in a file:

    `wc -l DiverseCas9s.faa`

#### Redirect data `>`
- The following command puts the output on the screen.

    `grep "gbkey=CDS" DiverseCas9s.faa`

- What if you want to store the output to another file?

    `grep "locus_tag=STER" DiverseCas9s.faa > Cas9sOutput.txt`

#### Append data `>>`
- What if you want to add the "" search results to your output file that already exists?

    `grep 'protein_id=YP' DiverseCas9s.faa >> Cas9sOutput.txt`

- If you only used the `>` the text that was already in the file would be overwritten.

#### Pipe `|`
- The `|` command (hit `Shift + \`) allows you to connect the output of one command to the next command.
- Save time and memory when programming!
- For example:
    `grep 'protein_id=YP' DiverseCas9s.faa | wc -l`

# Conclusion
- The ability to use and navigate with UNIX is essential.
- Our best friends: Google, `man`, or `<program name> -h`.
- Now, let's go to the `practice` directory and work on the practice problems with your group!


