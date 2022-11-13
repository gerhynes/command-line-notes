# Command Line Notes

Sources:
- [The Linux Command Line Bootcamp](https://www.udemy.com/course/the-linux-command-line-bootcamp/)

The command line gives you far more control over your machine. You can change permissions, view hidden files, interact with databases, start servers, manage processes and more.

Once you learn commands, you can perform tasks much faster than with a GUI. You can automate repetitive tasks that would take ages to do manually. You can also set up tasks to run at regular intervals or specific dates.

Most commands work on both Linux and MacOs and can be made to work on Windows with a little work.

Using the command line is basically a requirement as a web developer, data scientist, DevOps engineer, sysadmin, etc. Additionally, most cloud services are operated via a Command Line Interface (CLI).

## Operating Systems
Most operating systems can be grouped into two categories:
- The Microsoft NT descendents include Windows, XBox OS and Windows Phone/Mobile.
- Pretty much everything else has lineage going back to Unix, including MacOs, iOS, Linux, Android, Chrome OS and even PS5 OS.

### Unix
Unix was an operating system developed at Bell Labs in the mid 1960s. many of the innovations and design choices of the original unix team have lived on 50+ years later, including multi-user operating systems and hierarchical file systems.

Unix is the "grandfather" of many frequently-used operating systems today.

In the early days of computers, operating systems were tightly tied to specific handrware. Unix decoupled the two and was easily portable to other hardware.

The "Unix philosophy" emphasizes modular software design and the creation of small individual programs that can be combined to perform complex tasks.

- Write programs that do one thing and do it well
- Write programs to work together
- Write programs to handle text streams, because that is a universal interface

Today the name "UNIX" is a trademark of a global consortium called The Open Group. They maintain a set of standards called the Single UNIX Specification, whcih describes the core commands, features, interfaces, utilities, and more that define a UNIX operating system.

The Open Group will certify an operating system as fully UNIX compliant if it passes conformance tests. Companies must pay to be tested and must pay further to use the UNIX trademark.

Many operating systems are based on the original UNIX operating system and are compatible with the UNIX standards but are not considered UNIX because they have not been certified by The Open Group. Often this is because of financial considerations or ethical objections.

These operating systems are called Unix-like. They fully or mostly meet the specification but cannot legally use the UNIX name.

The original Unix manual from 1971 is available online. Common commands, such as `cat` and `find`, can be traced back to it.

### Linux
The Free Softwaremovement came about in the 1980s as a response to the proliferation of proprietary and restricted software. Think of "free speech" rather than "free beer".

The movement's philosophy is that the computers and software should not prevent cooperation between users, and instead should have the goal of liberating everyone in cyberspace.

According to the movement's main leader, Richard Stallman, "Users should have the freedom to run, copy, distribute, study, change and improve the software".

Richard Stallman was a leader in a group of developers who aimed to create Free Software alternatives to Unix.

In 1984 he began work on the GNU Project, with the goal of creating an operating system that included "everything useful that normally comes with a Unix system so that one could get along without any software that is not Free".

Another developer, Linus Torvalds, was working on creating his own kernel known as Linux. The kernel is the part of an OS that facilitates interactions between the hardware and software.

At the time, many GNU "pieces" were complete, but it lacked a kernel. Torvalds combined his kernel with the existing GNU components to create a full operating system.

A kernel is a computer program that forms the core of an operating system and manages critical tasks like:
- memory management
- task scheduling
- managing hardware

While a kernel is a critical piece, it is not the same as an operating system. An engine is the essential "core" of a car, but you can't drive an engine on its own.

Today the term Linux refers to both the kernel created by Linux Torvalds and all the software that is part of the Linux ecosystems.

Some users feel strongly that the name GNU/Linux should be use dinstead, as it properly reflects the GNU Project's contributions.

The Linux kernel is not a full-blown operating system. When people talk about a Linux-based OS, they are referring to Linux distributions.

Typically a Linux distribution bundles together a Linux kernel, GNU tools, documentation, a package manager, a window system, and desktop environment.

There are nearly 1,000 Linux distributions available. Some of the most popular include Fedora, Ubuntu, Debian and CentOS.

### Terminals, Shells and Bash
A shell is a computer interface to an OS. Shells expose the OS's services to human users or other programs.

The shell takes our commands and gives them to the OS to perform.

It's name a shell because it is the outer layer around the OS, like a shell around an oyster.

A terminal is a program that runs a shell. Originally terminals were physical devices but these days they are software applications.

On most Linux-based systems, the default shell program is Bash. There are many other shells, but Bash is currently the most popular.

Bash is an acronym for "Bourne-Again SHell", a reference to Stephen Bourne, the creator of Bash's direct ancestor shell, sh.

Bash runs on pretty much every version of Unix and Unix-like systems.

## Command Basics
When we open our terminal, we'll see our prompt which likely includes `username@machinename:~$` .

The prompt is what you'll see whenever the shell is ready to accept new input. If you type something invalid and hit enter, the shell will attempt to find a command with that name before telling you "command not found".

`clear` will clear your terminal window.

`date` will print the current date and time.

Commands are case sensitive, so `Date` is not the same as `date`. If you're using MacOs, come commands are not case sensitive but others are, so it's safest to assume all commands are.

`ncal` will display the current month's calendar. `ncal` stands for "new calendar". There is also a `cal` command that does the same thing, but `ncal` adds some fancier functionality.

Pressing the up arrow key will cycle through previous commands.

### Arguments
Most commands support multiple options that modify their behaviour. You can decide which options to include, if any, when you execute a command.

Similarly, many commands accept arguments which the commands uses or acts upon.

The terms "arguments" and "parameters" are often used interchangeably to refer to values that you provide to commands.

The `echo` command is extremely simple. It takes the arguments you provide to it and prints them out.

```bash
echo mwahahaha
```

The `ncal` command accepts values to control the specific month(s) and year it displays. 

If you specify only a year, `ncal` will print out the calendar for that entire year.

If you provide a month and a year, `ncal` will print only the month's calendar.

```bash
ncal 2021

ncal july 1969
```

### Options
Each command typically supports a host of options that you can choose to use when executing the command. These options modify the behviour of the command in predefined ways.

Options are prefixed by a dash.

```bash
# use Julian days, numbered from 1 Jan
ncal -j

# use Monday as the first day of the week
ncal -M 

# display previous, current and next month
ncal -3

# sort in reverse order
sort -r colors.txt
```

Some commands support a lowercase option and an uppercase option and they mean something different.

You can provide multiple options at once, such as `ncal -3 -h`. When you provide multiple options to a single command, you can use a shorter syntax. `ncal -3h`.

Some options also support equivalent long-format options that are usually full words prefixed with two dashes.

```bash
# prints the date in UTC
date -u

# also prints the date in UTC
date --universal

# sorts contents in reverse order
sort -r colors.txt

# also sorts contents in reverse order
sort --reverse colors.txt
```

To use multiple long-form options in a single command, we must write them out seperately with their own dashes.

We cannot combine long-form options in the same way we can with single character options.

```bash
sort --reverse --unique colors.txt

sort -ru colors.txt
```

### Options with Parameters
Some options require us to pass in an additional value. For example `ncal`'s `-A` option is used to display a certain number of months after a specific date.

For example, `ncal -A 1` will print the current month and one month afterwards. This can also be written as `ncal -A1`. `ncal -B1` will print the previous and current month.

```bash
# prints current and next month
ncal -A 1

# also prints current and next month
ncal -A1
```

We can combine multiple options and arguments. It's common to put options before arguments.

```bash
# prints 1 month before and 2 months after July 1969
ncal -B1 -A2 july 1969
```

## Getting Help
### Manual Pages
The **man pages**, short for manual pages, are a built-in form of documentation available on nearly all UNIX-like OSs.

The specific contents vary from one OS to another, but at a bare minimum the man pages include information on commands and their usage.

To run the specific piece of documentation associated with a given command, run `man COMMAND`.

For eample to learn more about the `ncal` command, run `man ncal`.

```
man echo

man ncal
```

This displays a lot of information that you can scroll through. If you hit **space** or **f**, it will scroll by one page. To go back, use **b**. You can quit by typing **q**. **h** will display a help screen.

You can search the document using `/pattern`, such as `/-w` to look up what `-w` means.

### Parsing Man Page Synopses
In general, each man page will follow this pattern:
- The title/name of the command with a short explanation of its purpose
- A synopsis of the command's syntax
- A Description of the command's options

Anything listed in square brackets is optional.

```bash
ncal [-31bhJeoSM] [-A number] [-B number] [-d yyyy-mm] [year]
```

An ellipses indicates that one or more of the proceeding operands are allowed:
- `[OPTION]...` means you can pass more than one option
- `[STRING]...` means you can pass multiple strings.

Some commands require certain arguments in order to run. Required operands are not wrapped in square brackets.

```bash
cp [OPTION]... SOURCE DEST
```

### Manual Sections and Searching
The manual is broken into 8 sections, each covering a specific topic in depth:
1. User Commands
2. System Calls
3. C Library Functions
4. Special Files
5. File Forms
6. Games
7. Miscellaneous
8. System Admin Commands

Sometimes you might find information with the same name located in different sections.

### `type` and `which`
There are really four types of commands:
- An executable program, usually stored in /bin, /usr/bin, or /usr/local/bin. These are compiled binary files, hence bin.
- A built-in shell command. These commands are part of the shell (bash or zsh)
- A shell function
- An alias

The `type` command will tell you the type of a command.

```bash
type clear 
# clear is hashed (/usr/bin/clear)

type cd
# cd is a shell builtin
```

The `which` command lets you find the exact location of an executable. This only works for executables, not built-in shell commands or aliases.

```bash
which clear
# /usr/bin/clear
```

### `help`
Some commands do not have man pages written for them, because they are commands that are directly built into the shell.

You can find documentation for these commands using the `help` command.

```bash
help cd
```

## Navigation
### The Root Directory
The root directory is the starting point for your entire filesystem. The actual name of the directory is `/`. 

Confusingly, there is a sub-directory called `root` that is not the same thing.

On desktop Linux `xdg-open /` will open the root directory in a GUI.

### The Home Directory
`/home` contains a home folder for each user on the system, such as `/home/priya` or `/home/lily`.

`/home/username` contains all of the files and data associated with that user.

`~` is a shortcut for referring to the currently logged-in user's home directory.

### `pwd`
The `pwd` (print working directory) command acts as a "where am I" command. It will print the path of your current working directory, starting from the root.

For example, running `pwd` from the desktop would show `/home/username/Desktop`.

```bash
pwd
```

### `ls`
The list command will list the contents of a directory.

When used with no options or arguments, it prints a list of the files and subfolders in the current directory.

You can also list the contents of a specific directory using `ls path`, for example `ls /bin` will print the contents of `/bin`.

```bash
ls

ls /home/username
```

The `ls` command accepts several options.

`ls -l` prints in long listing format. It shows far more information about each file or folder.

`ls -a` lists any hidden files that start with a `.`. These are normally not listed.

You can also combine options. `ls -la` prints detailed information for all files, including hidden files.

### Changing Directories with `cd`
The `cd` command is used to change the current working directory, "moving" into another directory.

For example, `cd /home/username` would move to the user's home directory.

In Unix-like OSes a single dot `.` is used to represent the current directory. Two dots `..` represent the parent directory. As such, you can use `cd ..` to move up one level, from your current directory into the parent directory.

```bash
cd Desktop
cd ..
```

`cd ../..` will move back up two directories.

`cd ~` will move to the home directory.

### Relative vs Absolute Paths
When providing paths to commands like `cd` or `ls`, you have the option to use relative or absolute paths.

**Relative paths** are paths that specify a directory/file relative to the current directory. For example, in the `/home` directory, you can use `cd username` to switch to the user's directory. But from the `/bin` directory, the relative path would be `../home/username`.

**Absolute paths** are paths that start from the root directory (they start with `/`). You can use absolute paths to specify a location no matter your current location. For example, from the `/bin` directory, you could use `cd /home/username` to change into the user's directory.

```bash
# relative
cd ../home/username

# absolute
cd /home/username
```

### Overview of Other Directories
The root directory contains a number of directories, including:
- `/bin` - contains executable programs you can run
- `/etc` - contains configuration files and initialization scripts
- `/media` - connects to removable media, such as USB drives
- `/var` - contains files for logging, outputs of othe programs, and caches
- `/root` - the home folder for the "root" superuser
- `/usr` - contains executable files, libraries, and programs

## Creating Files and Folders
### Creating Files with `touch`
Use `touch filename` to create a new file from the command line. If you try to use `touch` to create a file that already exists, it will simply update the access and modification dates to the current time.

You don't need to create the file in the current directory. You can provide a path to where you'd like the file to be created.

```bash
touch notes.txt

touch README.md

touch /home/username/document.txt
```

### File Types, Extensions and the `file` Command
The `file` command can be used to determine the file type of a specified file. 

It doesn't use the file extension to determine the file type, instead relying on things such as metadata.

```bash
file contract.pdf
# contract.pdf: PDF document, version 1.4
```

### Filenames
There are several characters (such as /, \, |, #, ?, :) that have special meanings to the shell and so shouldn't be used in filenames. Spaces should also be avoided in filenames.

The Linux filesystem treats file and directory names as case sensitive, so `app` and `App` will be recognized as different files.

### Creating Directories with `mkdir`
Use `mkdir foldername` to create a new directory. If you provide several foldernames, it will create them all in the same parent directory.

You can provide an absolute or relative path to the directory you want to create.

```bash
mkdir images styles

mkdir ~/games
```

You can use the `-p` option to create a parent directory at the same time.

```bash
mkdir -p components/navbar
```

## Nano
Nano (short for Nano's ANOther editor) is a simple text editor that you can access directly from the terminal. It's far more accessible than other command-line editors like vim or emacs.

Nano includes all the basic text editing functionality you would expect, such as search, spellcheck, and syntax highlighting. 

To open a file with nan, run `nano filename`. If the file doesn't exist it will be created once you save.

```bash
nano novel-first-draft.txt
```

To write your changes to the file, use `ctrl O`. To exit, use `ctrl X`.

Use `ctrl g` to open Nano's documentation. If you see `M` it refers to the meta key (`esc` on Macs and `alt` on Windows).

`alt /` and `alt \` lets you jump to the end or start of the file you're editing.

Bear in mind that Nano's commands often don't map to the shortcuts you might be used to.

To turn on line wrapping, use `alt $`.

Use `ctrl W` and then enter a search phrase to search forward in the file from your current cursor location. This is case insensitive. Use `ctrl C` to toggle case sensitivity.

To search and replace, use `ctrl \` and then enter the word you want to replace. Then enter the replacement and decide whether to replace specific matches or all matches.

You can enable spellchecking inside Nano in the config file located at `/etc/nanorc`. Use `ctrl T` to run spellcheck.

## Deleting, Copying, and Moving

### Deleting Files With `rm`
Use the `rm` (remove) command to remove files from your machine. You can remove multiple files at once by passing multiple filenames to `rm`.

`rm` permanently deletes files. There is no undo or recycling bin to retrieve them from.

```bash
rm filename

rm file1 file2 file3

rm path_to_file
```

### Deleting Folders with `-d` and `-r`
To delete empty folders, you need to use the `-d` option with `rm`. 

To delete folders that are not empty, use the `-r` (recursive) option. This will delete the directory and all the files inside it.

```bash
rm -d empty_directory

rm -r directory_with_contents
```

Be careful when deleting directories. The `-i` (interactive) option will prompt you before every removal.

### Moving Files with `mv`
Use `mv source destination` to move files and directories from one location to another.

When you specify a file or files as the source and a directory as the destination, you are moving the files into that directory. 

You can use relative or absolute paths with `mv`. The command won't work if the destination folder doesn't exist.

You can provide one or more source files but only one destination.

```bash
mv main.css styles/

mv temp.txt ~

mv file1 file2 file3 Desktop/
```

### Moving Folder with `mv`
When moving one folder into another, the destination folder must exist, otherwise `mv` will rename the source folder.

You can move multiple folders into one destinaton folder.

```bash
mv Cats/ Cleanup/

mv Chickens/ Dogs/ Hello/ Cleanup/

mv Dogs/ ..
```

### Renaming with `mv`
You can also use `mv` to rename single files and folders.

If you specify a single file as the source and a single file as the destination, it will rename the file. 

If you specify a single folder as the source and the destination doesn't yet exist, it will rename the folder. If the destination folder does exist, it will move the source folder into the destination folder.

```bash
mv chickens.txt roosters.txt
```

### Copying with `cp`
You can use the `cp` command to create copies of files and folders.

You need to use the `-r` option to copy directories recursively.

You can copy multiple source files into one destination folder.

```bash
cp sheep.txt dolly.txt

cp Cleanup/ CleanupBackup/ -r

cp file1 file2 dest/
```

## Shortcuts and History
The command line has several built-in shortcuts designded so your hands never have to leave your keyboard.

### Clearing and Jumping Lines
Use `ctrl l` to clear the entire screen.

Use `ctrl a` to move the cursor to the beginning of the line.

Use `ctrl e` to move the cursor to the end of the line.

### Jumping Characters and Words
Use `ctrl f` to move the cursor forward one character at a time (same as the right arrow key).

Use `ctrl b` to move the cursor backwards one character at a time (same as the left arrow key).

Use `alt f` to move the cursor forward one word.

Use `alt b` to move the cursor backwards one word.

### Swapping Characters and Words
Use `ctrl t` to swap the current character under the cursor with the one preceding it. This can be useful to quickly correct typos.

Use `alt t` to swap the current word with the preceding word.

### Killing Lines and Words
Use `ctrl k` to kill (delete) the text from the current cursor location until the end of the line.

Use `ctrl u` to kill (delete) the text from the current cursor location to the beginning of the line.

Use `alt d` to kill the text from the current cursor location to the end of the word.

Use `ctrl w` or `alt delete` to kill the text from the current cursor location to the beginning of the word.

### (Reviving Text) Yanking
When you kill text using commands like `ctrl k`, the killed text is stored in memory in an area known as the "kill-ring".

You can retrieve the most recently killed text using `ctrl y`.

### History and History Expansion
Bash keeps a record of the command you previously entered. You can see the actual file at `~/.bash_history`.

You can scroll through this history one command at a time using the up and down arrow keys.

You can also use the `history` command to view the entire history. It's generally easier to manage if you pipe the output to less.

```bash
history | less
```

You can easily re-run an earlier command if you have its line number from the history. For example, to run the 73rd command in the history, use `!73`. This is called history expansion.

You can use `!!` to re-reun the previous command and `!-n` to run the command n commands ago.

```bash
!73 # re-run the 73rd command

!! # re-run the last command

!-5 # re-run the 5th last command
```

Often it's easiest to find an earier command by searching using a small portion of the command that you remember.

Use `ctrl r` to enter "reverse-i-search". As you start typing, Bash will search the history and show you the best match. Hit `ctrl r` to cycle through potential matches.

### Working with Files
### The `cat` Command
`cat` concatenates and prints the contents of files.

`cat filename` will read the contents of a file and print them out. 

If you provide `cat` with multiple files, it will concatenate their contents and output them

```bash
cat file1 file2
```

### Working with `less`
The `less` command displays the contents of a file, one page at a time. You can navigate forwards and backwards through the file, which is especially useful for very large files.

```bash
less somefile.txt
```

When viewing a file using less:
- press `space` or `f` to go to the next page of the file
- press `b` to go back to the previous page
- press `enter` or `down arrow` to scroll by one line
- to search, type `/` followed by a pattern
- press `q` to quit

### `tac` and `rev`
`tac` (cat backwards) will concatenate and print files in reverse. It prints each line of a file, starting with the last line. You can think of it as printing in reverse "vertically".

```bash
tac file.txt
# third line
# second line
# first line
```

`rev` prints the contents of a file, reversing the order of each line. Think of it as a "horizontal reverse", where `tac` is a vertical reverse.

```bash
rev file.txt
# enil tsrif
# enil dnoces
# enil driht
```

### `head` and `tail`
`head` prints a portion of a file, starting from the beginning of the rile. By default, it prints the first 10 lines of a file.

```bash
head war_and_peace.txt
```

`tail` works similarly, printing the end of a file. By default it prints the last 10 lines of a file.

```bash
tail war_and_peace.txt
```

With both `head` and `tail` you can specify the number of lines to print using the `-n` (or `--lines`) option. There's a shorter syntax to specify an exact number of lines.

```bash
head -n 13 file.txt

head -3 file.txt
```

You can also provide a number of bytes, rather than lines, to print out using the `-c` option.

```bash
head -c 8 file.txt
```

### `wc`
The `wc` (wordcount) command tells you the number of words, lines, or bytes in files. By default, it prints out three numbers: the lines, words, and bytes in a file.

You can use the `-l` option to limit the output to the number of lines.

The `-w` option limits the output to the number of words in the file.

```bash
wc -l students.txt
```

### `sort`
The `sort` command outputs the sorted contents of a file. It doesn't change the file itself. By default, it will sort the lines of a file in alphabetical order case-insensitively.

The `-r` option reverses the sorting.

```bash
sort names.txt

sort -r names.txt
```

With numbers, `sort` compares each digit rather than the whole number, so 199.99 would come before 49.00. The `-n` options lets you sort numerically.

The `-u` (unique) option lets you sort without duplicates.

### Sorting By Field
You can specify a particular "column" (in the simplest case, seperated by spaces) that you want to sort by, using the `-k` option followed by a field number.

For example, `sort data.txt -nk 2` tells `sort` to use the numeric sort and to sort using the 2nd field in the file

```bash
sort data.txt -nk 2
# pencil 0.50 12
# pizza 5.99 1
# chocolate 10.99 1
```

## Redirection
### Standard Streams
The three standard streams are communication channels between a computer program and its environment.

They are:
- Standard Input
- Standard Output
- Standard Error

**Standard Input** is where a program or command gets its input information from. By default, the shell directs standard input from the keyboard. The input information could come from a keyboard, a file, or even from another command.

**Standard Output** is a place where a program or command can send information. The information could go to a screen to be displayed, to a file, or even to a printer or other device.

**Standard Error** is a destination for commands and programs to send error messages. By default, the shell directs standard error information to the screen for you to read, but you can change the destination if needed.

### Redirecting Standard Output
Redirection describes the ways you can alter the source of standard input, and the destinations for standard output and standard error.

The redirect output symbol `>` tells the shell to redirect the output of a command to a specific file instead of the screen. If the file already exists, it will be overwritten.

```bash
date > output.txt
```

### Appending Standard Output
When you redirect output into a file using `>` any existing contents in the file are overwritten. 

To instead keep the existing contents in the file and add new content to the end of the file, use `>>` when redirecting.

```bash
echo "hello" >> greeting.txt
echo "world" >> greeting.txt
cat greeting.txt
# hello
# world
```

### Redirecting Standard Input
To pass the contents of a file to standard input, use `<` followed by the filename.

```bash
cat < filename.txt
```

### Redirecting Standard Input and Standard Output Together
You can redirect standard input and output at the same time, for example to read in the contents of one file and redirect the output to another file.

```bash
cat < original.txt > output.txt

sort < names.txt > sorted.txt 
```

### Redirecting Standard Error
By default, error messages are output to the screen, but you can change this by redirecting standard error.

The standard error redirection operator is `2>`.  You can append the error using `2>>`. 

```bash
cat nonexistantfile 2> error.txt
```

Each stream gets its own numeric file descriptor:
- 0 - standard input
- 1 - standard output
- 2 - standard error

The `>` operator actually defaults to using 1 as the file descriptor number, which is why you don't need to specify `1>` to redirect standard output.

Similarly, the `<` operator uses a default file descriptor number of 0, so you don't need to specify `0<` to redirect to standard input (though you can).

```bash
date 1> now.txt
# equivalent to
date > now.txt
```

### Combining Redirection, and Fancy Sortcuts
You can redirect multiple streams at once, for example concatenating two files, redirecting standard output to one file and standard error to another.

Order matters: If you're going to redirect to both standard output and standard error, you need to do standard output first.

```bash
cat ants.txt bees.txt > insects.txt 2> error.txt
```

If you want to redirect both standard output and standard error to the same file, you could use `2>&1`. This tells the shell to redirect standard error to wherever standard output is redirected to.

```bash
ls docs > output.txt 2>&1
# equivalent to
ls docs > output.txt 2> output.txt
```

Newer versions of Bash also support syntax for redirecting both standard output and standard error to the same file using the `&>` notation.

```bash
ls docs &> output.txt

ls docs &>> output.txt
```

## Piping
You can use the pipe character `|` to separate two commands. The output of the first command will be passed to the standard input of the second command.

Pipes are used to redirect a stream from one program to another program. You can take the output of one command and redirect it to the input of another.

```bash
command1 | command2
```

For example, you could pipe the output of `ls` to `less`. Since the `/usr/bin` directory typically contains a bunch of stuff, it can be nice to use less to read the results in a more manageable way.

```bash
ls -l /usr/bin | less
```

Or to count the commands in `/usr/bin`.

```bash
ls /usr/bin -l | wc -l
```

### Comparing Redirecting and Piping
Though both the `>` character and the `|` character are used to redirect output, they do it in very different ways.

`>` connects a command to some file.

`|` connects a command to another command.

```bash
ls -l /usr/bin > list.txt

ls -l /usr/bin | less
```

### `tr`
The `tr` (translate) command requires you to provide data via standard input, you provide a set of characters that you want to match and a set of characters that you want to translate them to.

You can match one character, a set of characters, or use character classes.

The `-d` option lets you delete characters.

You can pipe from one `tr` to another.

```bash
# uppercase all s characters
cat msg.txt | tr s S

# uppercase all letters
cat msg.txt | tr a-z A-Z

# remove letters, colons and spaces
cata data.txt | tr -d [:alpha:] | tr -d : | tr -d [:blank:]
```

### Working with Multiple Pipes
You can combine multiple pipes together, passing the output of one pipe to the next.

```bash
# show lines 3-7 from a file
cat file | head -7 | tail -5

# show 3 largest files in current directory
ls -lh | sort -rhk 5 | head -3
```

### Using the `tee` Command
The `tee` command reads standard input and copies it both to standard output and to a file. This lets you capture information part of the way through a pipeline, without interrupting the flow.

```bash
command1 | tee file | command2

du -ha /usr/bin | sort -h | tee sizes.txt | head -3
```

## Expansion
### Wildcard Characters (Globbing Patterns)
You can use special wildcard characters to build patterns that can match multiple filenames at once.

The asterisk `*` charcter represents zero or more characters in a filename.

For example, `ls *.html` will match any files that end in .html, `cat blue` will match any files that start with "blue". You can combine multiple `*`s such as `cat *-log*`.

The question mark `?` character represents any single character.

For example, `ls app.??` will match any file called app that ends in a two character file extension, such as `app.js` or `app.py`. `ls pic?.png` will match `pic1.png` or `picA.png`.

### Range Wildcards
Inside square brackets `[]` you can specify a range of characters to match.

For example, `ls pic[123].png` will match any of pic1.png, pic2.png, pic3.png, `ls[A-F]*` will match any files that begin with A, B, C, D, E, or F.

### Tilde Expansion
If you reference `~` in a command it is coverted to a reference to your home directory.

```bash
echo ~
# /home/username

mv file.txt ~/subdirectory
```

### Brace Expansion
Brace expansion is used to generate arbitrary strings. Basically, it will generate multiple strings for you based on a pattern. You provide a set of strings inside of curly braces `{}` as well as optional surrounding prefixes and suffixes.

The specified strings are used to generate all possible combinations with the optional prefixes and suffixes.

For example, `touch page{1,2,3}.txt` will generate three new files: page1.txt, page2.txt, and page3.txt.

You can combine smultiple braces. For example the following will generate a file for the AM and PM of each weekday.

```bash
echo {Mon,Tues,Wed,Thurs,Fri}-{AM,PM}.txt
```

You can provide a numeric range, which will be used to generate a sequence. For example, `touch Jan{1..31}.txt`.

You can provide a third value which defines the interval for the range. For example, `echo {2..10..2}` will display 2, 4, 6, 8, and 10.

You can also specify alphabetical ranges. For example, `touch group-{a..e}.txt`

You can use ranges to quickly create directory structures.

```bash
mkdir -p {Mon,Tues,Wed,Thurs,Fri,Sat,Sun}/{Breakfast,Lunch,Dinner}.txt
```

You can used nested brace expansions.

```bash
echo {x,y{1..5},z}
# x y1 y2 y3 y4 y5 z
```

### Arithmetic Expansion
The shell will perform arithmetic via expansion using the `$((expression))` syntax. Inside the parentheses you can write arithmetic expressions using:
- + addition
- - subtraction
- * multiplication
- / division
- ** exponentiation
- % modulo (remainder)

The shell only performs integer arithmetic, so the result will always be a whole number.

```bash
echo $((10+7))
# 17

echo $((10/3))
# 3

echo $((10**3))
# 1000
```

### Quoting
On the command line, whitespace is ignored because the shell performs word splitting. The shell uses whitespace to distinguish between different command line arguments.

```bash
echo look at                          me
# look at me
```

If a word starts with a $, the shell will think you are referencing a variable. If it can't find a value for that variable, it will substitute an empty string.

```bash
echo holy $hit
# holy
```

If you wrap text in double quotes, the shell will respect your spacing and will ignore special characters, except for dollar sign, backslash and backtick.

Pathname expansion, brace expansion and word splitting will be ignored. However, command substitution and arithmetic expansion is still performed because dollar signs still have meaning inside double quotes.

```bash
echo "look at     me"
# look at     me

echo "{1..9}"
# {1..9}
```

You can use single quotes to suppress all forms of substitution.

```bash
echo "$((2+2)) is 4"
# 4 is 4

echo '$((2+2)) is 4'
# $((2+2)) is 4
```

### Command Substitution
You can use the `${command}` syntax to display the output of another command.

```bash
echo "today is ${date}"
# today is Thu 01 May 2021 03:10:31 PM PDT

# alernative syntax
echo "today is `date`"
# today is Thu 01 May 2021 03:10:31 PM PDT
```

## Finding Things
### The `locate` command
The `locate` command performs a search of pathnames across your machine that match a given substring and then prints out any matching names.

On Linux, you need to install it first, such as with `sudo apt-get install mlocate`.

It's fast because it uses a pre-generated database file rather than searching the entire machine. You can use `updatedb` to update this database, though it automatically does this daily. It also doesn't matter which directory you run the command from.

For example, `locate chick` will perform a search for all files that contain log in their name.

```bash
locate chick
# /home/colt/chicken.txt 
# /home/colt/demo/chick123
# /home/chickachickaboomboom
```

You can combine locate with wildcard characters.

```bash
locate /bin/less???
```

The `-e` option will only print entries that actually exist at the time locate is run.

The `-i` option tells locate to ignore case.

The `-l`, or `--limit`, option will limit the number of entries that locate retrieves. 

### The `find` Command
`find` is far more powerful, but slower, than `locate`. Unlike `locate`, it doesn't use a database.

By default, `find` on its own will list every single file and directory nested in your current working directory.

You can also provide a specific folder. For example, `find friends/` would print all the files and sub-directories inside the friends directory (including nested folders).

You can tell `find` to only find by file type: only print files, directories, symbolic links, using the `-type` option.

`find -type f` will limit the search to files

`find -type d` will limit the search to directories.

You can provide a specific pattern for `find` to use when matching filenames and directories with the `-name` option. You need to enclose your pattern in quotes.

For example, to find all files on your Desktop that end in the .txt extension, you could run `find ~/Desktop -name "*.txt"`. Use the `-iname` option for case-insensitive searching.

You can use the `-size` option to find files of a specific size. For example, to find all files larger than 1 gigabyte, you could use `find -size +1G`, to find all files under 50 megabytes, you could use `find -size -50M`. To find files that are exactly 20 kilobytes, you could use `find -size 20K`.

You can use the `-user` option to match files and directories rhat belong to a particular user. 

```bash
find -user mary
```

### Timestamps
`mtime`, or modification time, is when a file's contents were last modified.

`ctime`, or change time, is when a file was last changed. This occurs anytime mtime changes but also when you rename a file, move it, or alter permissions.

`atime`, or access time, is updated when a file is ready by an application or a command like `cat`.

You can view these timestamps using:
- `ls -l` - for last modified
- `ls -lc` - for last changed
- `ls -lu` - for last accessed

You can combine `find` with timestamps.

`find -mmin -30` - finds files modified less than 30 minutes ago.

`find -amin -1` finds files that were accessed less than 1 minute ago.

`find -cmin +60` finds files that were changed more than 60 minutes ago.

`min` refers to n minutes ago.

`time` refers to n 24-hour periods ago (it doesn't map exactly onto days)

`find -mtime -5` finds files modified within the past 5 24-hour periods.

### `find` with Logical Operators
You can use the `-and`, `-or`, and `-not` operators to create more complex queries.

```bash
find -name "*chick*" -or -name "*kitty*"

# find all files that aren't HTML
find -type -f -not -name "*.html"
```

### `find` with `-exec` and User-Defined Actions
You can provide `find` with your own action to perform using each matching pathname.

The syntax is `find -exec command {};`

The {} are placeholders for the current pathname (each match), and the semicolon is required to indicate the end of the command.

You need to wrap the {} and ; in quotes because those characters have special meanings otherwise.

To delete every file that contains "broken" in its filename, you could run.

```bash
find -name "*broken*" -exec rm '{}' ';'

# Copy all HTML files and append _COPY to their filenames
find -type f -name "*.html" -exec cp '{}' '{}_COPY' ';'
```

If you replace `-exec` with `-ok`, you will be asked for confirmation before each command is executed. This might be a good idea if you're removing files, for example.

### The `xargs` command
When you provide a command via `-exec`, that command is executed seperately for every single element. You can instead use a special command, `xargs`, to build up the input into a bundle that will be provided as an argument list to the next command.

`xargs` is used to take standard input and transform it into an argument list that can then be provided in a pipeline to a command that doesn't accept standard input.

```bash
find -name "*.txt" -exec ls '{}' ';'
# or
find -name "*.txt" | xargs ls
```

## Grep
The `grep` command searches for patterns in each file's contents. Grep will print each line that matches a pattern we provide.

```bash
grep pattern filename
```

For example, `grep "chicken" animals.txt` will print each line from the animals.txt file that contains the pattern "chicken".

Use the `-i` option to make the search case insensitive.

```bash
grep -i "Chapter" book.txt
```

Use the `-w` option to ensure that `grep` only matches words, rather than fragments located inside of words. A word is define dby non-word characters on either side (start of line, spaces, end of line, punctuation).

```bash
grep -w "cat" book.txt
```

You can use the `-r` option to perform a recursive search, which will include all fiels under a directory, subdirectories and their files, and so on.

If you don't specify a starting directory, `grep` will search the current working directory and any nested directories.

```bash
grep -r "chicken"
```

You can use `[]` to match multiple patterns.

```bash
# I can't spell relevant
grep -r "rel[ea]v[ea]nt"
```

### `grep` options
You can count the number of matches using the `-c` option.

```bash
grep "myself" SongOfMyself.txt -i -c

grep "I" SongOfMyself.txt -w -c
```

The `-B` and `-A` options will give you n number of lines before or after each match. `-C` will give you lines on each side of the match.

```bash
grep "grass" SongOfMyself.txt -c -B1

grep "grass" SongOfMyself.txt -c -A5
```

The `-n` option will prefix each line of output with its line number.

```bash
grep "Section 6" SongOfMyself.txt -n
```

The `-m` option lets you specify the first n number of matches to display.

```bash
grep "wagon" SongOfMyself.txt -m1
```

### Regular Expressions
You can provide regular expressions to `grep`. Regular expressions help you match complex patterns, but the syntax can be... challenging.

- `.`- matches any single character
- `^` - matches the start of a line
- `$` - matches the end of a line
- `[abc]` - matches any character in the set
- `[^abc]` - matches any character not in the set
- `[A-Z]` - matches characters in a range
- `*` - repeat previous expression 0 or more times
- `\` - escape meta-characters

```bash
# matches 5 letter words beginning with p
grep "p...." SongOfMyself.txt -w

# matches lines that start with I
grep "^I" SongOfMyself.txt -w

# matches lines that end with )
grep ")$" SongOfMyself.txt -c
```

The `-E` option interprets patterns as extended regular expressions, letting you use characters such as `?` that have a meaning in the shell outside of regular expressions.

```bash
# matches birds? exactly
grep "birds?" SongOfMyself.txt -w

# matches bird or birds
grep "birds?" SongOfMyself.txt -w -E

# matches words with 3 consecutive vowels
grep "[aeiou]{3}" -E SongOfMyself.txt
```

### Piping to `grep`
A common use case is to use `grep` to whittle down or filter a large chunk of data.

For example, `ps -aux | grep sound` will output a list of all processes running on the machine that mention sound. 

You can use `grep` to search the man page of a command for specific words or options.

```bash
man grep | grep "count" -i
```

You can use `find` to narrow down a selection of files to use `grep` on.

```bash
find ~ -name "*.txt" ! -empty -type f -exec grep -ln "purple" '{}' ';'
```

You could use `grep` with a complex regular expression to find every URL in a directory of files.

```bash
grep -rE "https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)" ~ -I
```

## Permissions
Unix-like systems are multiuser OSes. More than one person can be using the same computer at the same time (though this is difficult today with usually only one display and keyboard).

Way back when computers were ridiculously expensive, massive machines, a university might only have one computer but dozens of terminals across campus.

One user can read another user's files but can't create or edit them by default.

### Groups
On Unix-like systems, a single user may be the owner of files and directories, meaning that they have control over their access.

Additionally, users can belong to groups which are given access to particular files and folders by their owners. 

For example, on Ubuntu when you create a new user the default group for that user will have the same name.

### File Attributes
File attributes, printed first when you `ls -l` in a directory, tell you the type of the file, the read, write, and execute permissions for the file's owner, the file's group owner, and everyone else.

```bash
-rw-rw-r--
```

The first character indicates the type of the file, such as:

- `-` regular file
- `d` - directory
- `c` - character special file
- `l` - symbolic link
- `b` - block files

The next nine characters are broken into three groupings. They describe read permission, write permission, and execute permission, such as:
- Owner - `rwx`
- Group - `rw-`
- World - `r--`

The first character in a grouping is always either `r` (has read permissions) or `-` (doesn't have read permissions).

The second character in a grouping is always either `w` (has write permissions) or `-` (doesn't have write permissions).

The third character in a grouping is always either `x` (has execute permissions) or `-` (doesn't have execute permissions).

If you give a file execute permission, it means you can run it as a program.

|**Character**| **Effect on Files**| **Effect on Directories**|
|--|--|---|
|r|file can be read|directory's contents can be listed|
|w|file can be modified|directory's contents can be modified but only if the executable attribute is also set|
|x|file can be treated as a program to be executed|allows a directory to be entered or cd'ed into|
|-|file cannot be read, modified, or executed depending on the location of the `-` character|directory contents cannot be shown, modified, or cd'ed into depending on the location of the `-` character|

## Altering Permissions
### The `chmod` Command - Symbolic Notation
To change the permissions of a file or directory, you can use the `chmod` (change mode) command.

```bash
chmod mode file
```

To use `chmod` to alter permissions, you need to tell it:
- Who you are changing permissions for
- What change you are making (adding/removing)
- Which permissions you are setting

```bash
# add write permissions to the group
chmod g+w file.txt

# remove write permissions from all
chmod a-w file.txt
```

When specifying permissions with `chmod`, you use a special syntax to write permission statements.

First, specify the "who" using:
- u - user (the owner of the file)
- g - group (members of the group the file belongs to)
- o - others (the "world")
- a - all of the above

Next, tell `chmod` "what" you are doing:
- - (minus sign) removes the permission
- + (plus sign) grants the permission
- = (equals sign) set a permission and remove others

Finally, the "which" values are:
- r - the read permission
- w - the write permission
- x - the execute permission

```bash
# add execute permissions for owner
chmod u+x file.txt

# set permissions to read only for all
chmod a=r file.txt
```

### `chmod` - Octal Notation
`chmod` also supports another way of representing permission patterns: octal numbers (base 8). Each digit in an octal number represents 3 binary digits.

|Octal|Binary|File Mode|
|---|---|---|
|0|000|`---`|
|1|001|--x|
|2|010|-w-|
|3|011|-wx|
|4|100|r--|
|5|101|r-x|
|6|110|rw-|
|7|111|rwx|

```bash
# rwx r-x r-x 
chmod 755 file.txt
```

### The `su` Command - Substitute User
There may be times when you want to start a shell as another user, from within your own shell session. You can use the `su` (substitute user) command to do that.

```bash
su - username
```

`su - julie` would create a new login shell for the user julie. You would need to enter julie's password. To leave the session, type `exit`.

You can be logged in as one user in one window and another user in another.

`su username` will will not change the current directory and will only set the environmen variables `HOME`, `SHELL`, `USER`, `LOGNAME`. It's recommended to always use `-` to avoid side effects caused by mixing environments.

### Root User
In Linux systems, there is a super user called root. The root user can run any command and access any file on the machine, regardless of the file's actual owner.

The root user has a lot of power and could easily damage or even destroy the system by running the wrong commands. For this reason, Ubuntu locks the root user by default.

If you run `ls -l` in the root directory, you'll see that the owner of everything in this direcotry is "root".

### The `sudo` Command
Even if the root user is locked by default, you can still run specific commands as the root user by using the `sudo` command.

Individual users are granted an "allowed" list of commands they can run as the super user.

Run `sudo -l` to see the permitted commands for your particular user.

To run a command as the root user, prefix it with `sudo`.

```bash
sudo apt-get update
```

### Changing Owners with `chown`
The `chown` command is used to change the onwer and/or the group owner of a specific file or directory.

```bash
chown joe file.txt
```

Regular users cannot change owners, so you need to prefix it with `sudo`.

To change the owner of a file and the file group owner at once, you can provide both using `chown user:group file`.

```bash
chown joe:teachers file.txt
```

### Working with Groups
To view the groups that a given user belongs to, run `groups USERNAME`.

```bash
groups colt
```

You can create new groups using the `addgroup` command. Only the root user can add groups.

```bash
addgroup friends
```

To add a user to a group, use the `adduser` command.

```bash
adduser colt friends
```

You can change group assignments for directories. When you do, you need to log out to have them take effect.

```bash
sudo chmod 770 SharedDirectory/
```

## The Environment
The shell maintains a set of information during a shell session known as the environment. It's a series of key-value pairs that define properties like:
- Your home directory
- Your working directory
- The name of your shell
- The name of the logged in user

Use the `printenv` command to view the environment variables and their current values. There are quite a few variables so it might be easier to read if piped to less.

```bash
printenv | less
```

### Parameter Expansion
If you write out the name of an environment variable prefixed with a $, the shell will replace it with the actual value.

For example, `echo $USER` results in the `USER` variable's value.

```bash
echo USER
# USER

echo $USER
# colt
```

### Defining and Exporting Variables
To define a variable, use the syntax `variable=value`. You will need to use quotes if the variable includes spaces.

Built-in variables are uppercased so it's a common convention to lowercase custom variables to prevent confusion.

Shell variables only exist in your current shell session.

```bash
color="purple"
name="sophie ota"
num=821
```

You can turn a shell variable into an environment variable using `export`.

```bash
export color="purple"
export name="sophie ota"
export num=821
```

### Startup Files
When you log in, the shell reads information from startup files. First the shell reads from global config files that effect the environment for all users. Then, the shell reads startup files for specific users.

The specific files the shell reads from depends on the type of the shell session: login vs non-login.

For login sessions:
- `etc/profile` - global config for all users
- `~/.bash_profile` - user's personal config file
- `~/.bash_login` - read if `bash_profile` isn't found
- `~/.profile` - used if the previous two aren't found

For non-login sessions (typical sessions when you launch the terminal via a GUI):
- `etc/bash.bashrc` - global config for all users
- `~/.bashrc` - specific settings for each user. This is where you can define your own settings and configuration.

### Customizing Your Prompt
You can change your shell's prompt by updating the `PS1` environment variable in your `.bashrc` file. The syntax is not terribly intuitive.

For example, the following will change the prompt to be the username, path to current directory and $:

```bash
export PS1="\u\w\\$ "
```

You can customize foreground and background colours, fonts and font weight.

### Defining Aliases
You can define your own commands using the `alias` keyword.

```bash
alias ll='ls -al'

alias ..='cd ..'
```

You can use the `type` command to fidn out what an alias refers to.

```bash
type l
# l is aliased to 'ls -CF'
```

Aliases should be defined in your `.bashrc` so that they persist between shell sessions.

Some commands may be already aliased, such as `ls` aliased to `ls --color=auto` so that you get coloured output.

Some aliases you might want could include:

```bash
alias mv='mv -v'
alias rm='rm -vi'
alias cp='cp -v'
```

You might want to put all your aliases in their own file `~/.bash_aliases` that will then be referenced in `bashrc`.

It's advisable to include comments to explain any of the more complicated aliases you use.

## Bash Scripting
You can create files containing Bash commands to be executed at a later date.

There are additional programming concepts that you probably won't use directly on the command line but will use in scripting, such as conditional logic and functions.

The basic steps are:
1. Write a script in a file and save it
2. Make the script executable using `chmod`
3. Verify that the shell can find your script

The first line of your script needs to be `#!/bin/bash`

The `#!` is called a shebang, and is used to tell the OS which interpreter it should use when parsing this file. In this case it's Bash.

After the shebang, you need to include the path to the Bash binary. This is not Bash specific. If you wanted to write a Python script, you would need to include the path to the Python binary.

Lines that begin with `#` will not be read by the shell. You can use these to write comments. 

```bash
#!/bin/bash

# my first script
echo "Hello there, $USER"
echo "Today is $(date)"
echo "Last ran hi at $(date)" >> hi.log
```

You can execute your script file using `bash filename` if you're in the same directory as it.

### The `PATH` Variable
When you run a command like `pwd`, the shell starts looking for the executable `pwd` program in the list of directories stored in the `PATH` variable.

It starts looking in the first location and then keeps looking if it doesn't find it.

If you want the shell to find your programs, you need to make sure you put them in a folder that is in the `PATH` variable.

A common place to put user-defined programs is in a bin folder located in the user's home directory, for example `/home/nick/bin`.

Some Linux distributions will automatically add file that are in `home/username/bin` to the `PATH`.

If that directory is not yet part of your path, you can add it by putting `PATH="$HOME/bin:$PATH"` in your .bashrc file. 

### Making a Script Executable
The next step is to make the file containing your script executable. `chmod a+x file` will grant executable permissions to everyone.

```bash
chmod a+x file
```

### Writing a Weather Script
Bash scripts can include conditional logic, for example to decide which parameters to include when using the `curl` command to make HTTP requests to an API endpoint.

```bash
#!/bin/bash

case $1 in
-h | --help)
  echo "WELCOME TO WEATHER HELP"
  echo "-3 for next 3 days of weather"
  ;;
-3)
  echo "YOU PROVIDED -3"
  curl "wttr.in"
  ;;
-l | --location)
  curl "wttr.in/$2"
  ;;
*)
  curl "wttr.in?m1"
  ;;
esac
```

## Cron
The `cron` service lets you schedule commands to run at regular intervals, such as: 
- every 30 minutes
- every day at midnight
- every 1st of the month
- every 15th December

To set up a cron job you need to edit the `crontab` configuration file. Rather than edit the file directly, it's best to use the `crontab -e` command.

The `crontab` command lets you maintain crontab files for individual users. The files temselves are located in `var/spool/cron/crontabs`.

The cron syntax is not very intuitive.

```bash
a b c d e command
```

- a - minute 0-59
- b - hour 0-23
- c - day (of month) 1-31
- d - month 1-12
- e - day (of week) 0-6

Cron characters can be:
- `*` - any value
- 5,6 - list of values
- 1-4 - range of values
- `*/5` - step values (every 5)

```bash
0 4 8-14 * *
```

For example, run a job at minute 30, every hour (every time the clock shows x:30)

```bash
30 * * * * command
```

To run a job every day at midnight (when the hour and minute is 0)

```bash
0 0 * * * command
```

To run a job every day at 6.30 am (when the hour is 6 and the minute is 30)

```bash
30 6 * * * command
```

To run a job every Monday at 6.30 am

```bash
30 6 * * 1 command
```

To run a job at midnight on the first of every month

```bash
0 0 1 * * command
```

To run a job every 10 minutes

```bash
*/10 * * * * command 
```

To run a job every hour on the hour from 9am-5pm

```bash
0 9-17 * * * command
```

https://crontab.guru is a good source of common cron examples.

### Handling Errors in a Cron Job
You can handle errors in cron jobs by redirecting the error to either the same output or a specific error file.

```bash
# send errors to the same file
* * * * * echo "Another minute" >> ~/time.log 2>&1
```

### Writing a File Backup Cron Job
You can use the `tar` command to archive directories and files.

```bash
#!/bin/bash
DATE=$(date +%d-%m-%Y)
BACKUP_DIR="/home/colt/backups"

tar -cvzf $BACKUP_DIR/backup-$DATE.tar.gz /home/colt/Desktop
```

```bash
# run every day at 3am
0 3 * * * /home/colt/bin/my-backup
```