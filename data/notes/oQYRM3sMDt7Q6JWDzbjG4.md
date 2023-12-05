
## Shell vs Terminal

- kernel - server
- shell - middleware
- terminal - client

## shell prompt

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$</code> at the end of the prompt ⇒ normal user
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">#</code> at the end of the prompt ⇒ root user
    - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">sudo su</code> to open a terminal as a root user

## shell functions

- they are built-in programs stored on our file system
- the shell searches for these programs through the <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">PATH</code> environment variable
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">which</code> gives the path of the program that would be executed for a particular command

## environment variables

- variables that are automatically set when you start the shell
- example: <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">path</code>

## interesting stuff from [missing semester](https://missing.csail.mit.edu/2020/course-shell/)

- almost all files in <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">/bin</code> have a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">x</code> permission set for the last group
    - so that anyone can execute those programs
- sudo - do as su(superuser)
- using the sys directory we can interact and do cool stuff with hardware
  - [controling the backlit programtically](https://missing.csail.mit.edu/2020/course-shell/#:~:text=a%20versatile%20and%20powerful%20tool)
  
## flags vs options

- if we pass some value with a flag - option
- here <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">-p</code> (don't follow symlinks) is a flag and <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">iname</code> is an option

```bash
find -P -iname '*some_string*'
```

## streams

- in shell, every program have input and output streams, by default set to terminal
- this can be configured using <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">< file</code> and <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">> file</code>
- this  command reads from hello1 and writes to hello2

```bash
cat < hello1.txt > hello2.txt
```

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">>> file</code> will append instead of overwriting to a file
- can be also used for streaming media files when combined with [chormecast](https://vitux.com/how-to-cast-video-from-ubuntu-to-chromecast/)

## strings

- defined with <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">'</code> are string literals
- defined with <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">"</code> will expand and substitute variables
- [bash quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)

## special variable in bash scripting

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$0</code> - Name of the script
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$1</code>to <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$9</code> - Arguments to the script. <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$1</code> is the first argument and so on.
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$@</code> - All the arguments
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$#</code> - Number of arguments
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$?</code> - Return code of the previous command
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$$</code> - Process identification number (PID) for the current script
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">!!</code> - Entire last command, including arguments
    - can be useful if we realize that the command needs root privileges after executing it for the first time
    - just type <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">sudo !!</code> followed by a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">tab</code>
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">$_</code> - Last argument from the last command

## exit codes and short-circuiting

```bash
false || echo "Oops, fail"
# Oops, fail

true || echo "Will not be printed"
#

true && echo "Things went well"
# Things went well

false && echo "Will not be printed"
#

true ; echo "This will always run"
# This will always run

false ; echo "This will always run"
# This will always run
```

## wildstars and globbing

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">?</code> - to match one character only
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">*</code> - to match any amount of characters
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">{}</code> - expand command using a list of arguments

```bash
convert image.{png,jpg}
# Will expand to
convert image.png image.jpg

# Globbing techniques can also be combined

# This will move all *.py and *.sh files
mv *{.py,.sh} folder

mkdir foo bar
# This creates files foo/a, foo/b, ... foo/h, bar/a, bar/b, ... bar/h
touch {foo,bar}/{a..h}
touch foo/x bar/y

# Show differences between files in foo and bar
diff <(ls foo) <(ls bar)
# Outputs
# < x
# ---
# > y
```

## scripting vs functions

- functions should be in the same language
- scripts can be in any language
  - env can be specified using the <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">shebang</code>
  - a good practice is to give env name as an argument, rather than the direct path    
  - ```bash
    #! usr/bin/env env_name
    ```
<br>

- functions are loaded only for the first time ⇒ they are faster
- scripts are loaded every time they are executed

<br>

- functions are loaded in the current shell environment
    - functions can modify environment variables
- scripts are executed in their separate processes

## tools

- [ ] <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">TLDR</code> pages or <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">bro</code> pages instead of <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">man</code> pages
- [ ] for finding and performing ops on file
    - [ ] <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">find</code> command
    - [ ] <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">fd</code> - better alternative
    - [ ] <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">locate</code> - uses indexing


