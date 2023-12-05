
## Shell vs Terminal

- kernel - server
- shell - middleware
- terminal - client

## Directory Structure

![](/assets/images/2023-01-05-18-13-15.png)

### `/bin`

- contains binaries and executable programs
- most of the command that we use are inside this directory

<blockquote style="background-color: #FF313120; padding:4px 3px; border-radius: 5px; border-left: 0.25em solid #FF3131; padding-left: 0.75em">cd is not a binary, it is built in shell command</blockquote>

- `/sbin` contains kernel mode binaries

### `/boot`

- contains static boot loader files
- `GRUB` files are here
  
### `/var`

- contains log files, packages and database files

### `/usr` - user system resources

- non-essential binaries are here

### `/dev`

- terminal devices, disk drives, USB's are included here

### `/etc`

- contains system configuration files
- should be text files, cannot be executables

### `/mnt`

- all external drivers are available here

## Shell Variable

- default datatype is string
- are accessed using `$`

### Some builtins

- `PATH`
- `?`: returns the status code of last-entered command

## A Script file

<blockquote style="background-color: #0096FF20; padding:4px 3px; border-radius: 5px; border-left: 0.25em solid #0096FF; padding-left: 0.75em">in linux, extension does not matter</blockquote>

- kernel uses the interpreter mentioned in the `shebang`

```bash
!# usr/bin/env bash
```

- status code of script is the status code of the last executed command

## Trivia

- bash: bourne again shell
- pwd: print working directory

## Some useful manuals

- `man`
- `whatis`: one line description of commands
- `apropos`: when you don't know the exact spelling

## Access Right Code

![](/assets/images/2023-01-05-18-31-23.png)

- meaning for files
  - `r`: can read and copy
  - `w`: can change the file
  - `x`: can execute the file
- meaning for directory
  - `r`: can list files in the directory
  - `w`: can delete / move files in the directory
  - `x`: can access files, provide you have access to those individual files

## Foreground and Background processes

[stackexchange](https://unix.stackexchange.com/questions/175741/what-is-background-and-foreground-processes-in-jobs)

- first answer
