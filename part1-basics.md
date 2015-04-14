Command Line Basics
===================

What is the Command Line Interface?
-----------------------------------
Underneath the wonderful Mac Graphical User Interface ("GUI") is a powerful and flexible method of working directly with files and the web. This is known as the "command line interface", or sometimes "CLI".

It may seem geeky at first, and its depth may seem intimidating, but you don't need to learn it all of it for it for the command line to become quite useful to you. In particular, in order to learn how to program web applications or clients effectively on the Mac, you will need to have some comfort with the basics of the Mac command line.

The Terminal, the Console, the Shell, and the Command Line
----------------------------------------------------------
First, you should learn how to start the built-in application that runs the Mac CLI, called the _Terminal_. To launch it, rather than the usual GUI method of opening the Applications/Utilities directory and double-clicking the Terminal app, instead you should learn to launch the Terminal soley by using your keyboard.

Type `command + spacebar` and then type `terminal` and press return. In fact, you don't even need to typically type the whole word -- just the first few letters `ter` or `term` is usually enough.

When Terminal first opens, you should see a small window with this text in it:

```
Last login: {some date} on console
{your computer name}:~ {your user name}$ 🁢
```
The window you see is created by the _Terminal_ application, which more properly a form of _terminal emulator_ and its contents (any commands and the text output from previous commands) are known as the _console_. These words come from the days when you had a greent CRT screen and keyboard –- the machine as a whole was the the _terminal_, and the contents of the screen was the _console_. Our _terminal emulator_ provides us the experience of typing into an old school terminal from the convenience of our modern graphical operating system.

The text before and including the $ is known as the _prompt_. The _command line_ is everything after the current prompt, and is the portion of the console where you can type.

The 🁢 symbol is the location of your _text cursor_ on the command line. Anything you type will appear under the text cursor and the text cursor will move to the next spot.

All the text you see in the console was created by what is known as the _shell_ application (the Mac defaults to the shell application known as _bash_).

Often the words terminal, console, command line, shell, or bash are used interchangably, but these each are are all slightly different. 

Someday you may want to switch to a more sophisticated Terminal applications (_iTerm_ is popular), or switch to a more sophisted text shell (_tsch_ is popular), or both. For the purpose of this _Intro to the Command Line_ tutorial we will only be using the default Mac _Terminal_ app, and the _bash_ command line text shell.

Running a Command
-----------------

If you now type the text `ls -l ~` you will see the text appear to the right of the $. This is your _command_. Type return to _execute_ your command.

```
{your computer name}:~ {your user name}$ ls -l ~
total 0
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Desktop
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Documents
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Downloads
drwx------@ 43 {your user name}  staff  1462 Apr 12 00:15 Library
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Movies
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Music
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Pictures
drwxr-xr-x+  5 {your user name}  staff   170 Oct 21 18:44 Public
{your computer name}:~ {your user name}$ 🁢
```

Nearly all commands follow a common pattern with 3 main parts. The program, the options, and the arguments, each seperated by spaces.

The program is the verb, in this case the first part `ls`, which is short for _list_, which will show us a list of files.

The options are like the adverb, and modify how the program is run. Options almost always begin with a hyphen. In this example `-l` means _long_, so the `ls` command will now show us more detailed information rather than just the names of the files.

The arguments are what is left, and are the objects of our command. They describe what we want our program to act on. In this case we are using a special shorthand name for our home directory `~`. 

Combined, these three parts tell the computer to list, in long form, the contents of your home directory.

The Current Directory
---------------------

When you enter many commands without any arguments, they will act by default on on the current directory (aka folder) . What is the current directory? Type `pwd`.

```
{your computer name}:~ {your user name}$ pwd
/Users/{your user name}
{your computer name}:~ {your user name}$ 🁢
```

The command `pwd` is short for 'present working directory' which basically means "Where am I now?". The result of `pwd` is the _path_ to where any commands without arguments will default to.

```
{your computer name}:~ {your user name}$ ls
Desktop		Downloads	Movies		Pictures
Documents	Library		Music		Public
{your computer name}:~ {your user name}$ 🁢
```

Notice that the `ls` command showed us one additional directory that you can't see from your Mac's Finder GUI: the Library directory. There can be other invisible files. We can see these by adding to the `ls` command an option, in this case `-a`.  Together the command and option `ls -a` means 'list all'.

```
{your computer name}:~ {your user name}$ ls
.			Desktop			Movies
..			Documents		Music
.CFUserTextEncoding	Downloads		Pictures
.Trash			Library			Public
{your computer name}:~ {your user name}$ 🁢
```

The 'ls -a' command reveals a number of directory and files that are marked as invisible to the Finder and the Mac GUI. Any file or directory that begins with a period will also be invisible to the Finder. We will learn more about these files later.

To look at the contents of another directory, you can add a _path_ option to the `ls` command. Type `ls Public` to see the contents of your Public directory (the name of the directory `Public` is case sensitive — `public` will not work).

```
{your computer name}:~ {your user name}$ ls Public
Drop Box
{your computer name}:~ {your user name}$ 🁢
```

The `ls -l` (i.e. `list long`) command lists additional information about each item in the current directory:

```
{your computer name}:~ {your user name}$ ls -l
total 0
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Desktop
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Documents
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Downloads
drwx------@ 43 {your user name}  staff  1462 Apr 12 00:15 Library
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Movies
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Music
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Pictures
drwxr-xr-x+  5 {your user name}  staff   170 Oct 21 18:44 Public
{your computer name}:~ {your user name}$ 🁢
```

With the `-l` option the `d` on the left tells you that the item in the directory contains another directory. A hyphen `-` tells you that the item is a file.

You can combine options, so `ls -la` will list all the information about all the contents of the current directory, including hidden dot `.` files and invisible directories like the `Library`.

```
{your computer name}:~ {your user name}$ ls -l
total 8
drwxr-xr-x+ 14 {your user name}  staff   476 Apr 12 12:39 .
drwxr-xr-x   6 root          admin   204 Oct 21 18:44 ..
-r--------   1 {your user name}  staff     7 Oct 21 18:46 .CFUserTextEncoding
drwx------   2 {your user name}  staff    68 Apr 11 23:27 .Trash
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Desktop
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Documents
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Downloads
drwx------@ 43 {your user name}  staff  1462 Apr 12 00:15 Library
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Movies
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Music
drwx------+  3 {your user name}  staff   102 Oct 21 18:44 Pictures
drwxr-xr-x+  5 {your user name}  staff   170 Oct 21 18:44 Public
{your computer name}:~ {your user name}$ 🁢
```

You can also add the name of a directory as an arguement to see the contents of that directory, for example `ls -la Public`

```
{your computer name}:~ {your user name}$ ls -la Public
total 0
drwxr-xr-x+  5 ChristopherA  staff  170 Oct 21 18:44 .
drwxr-xr-x+ 13 ChristopherA  staff  442 Apr 12 12:41 ..
-rw-r--r--   1 ChristopherA  staff    0 Oct 21 18:44 .com.apple.timemachine.supported
-rw-r--r--   1 ChristopherA  staff    0 Oct 21 18:44 .localized
drwx-wx-wx+  3 ChristopherA  staff  102 Oct 21 18:44 Drop Box
{your computer name}:~ {your user name}$ 🁢
```

Tab Completion
--------------

A useful feature that the command line offers is called "command line completion" or "tab completion". What this means if you enter insufficient information about an argument, you can press the `tab` key to see what the choices are, or if there is only one choice, select that one.

Try this out by typing `ls M` then press the `tab` key instead of return.

```
{your computer name}:~ {your user name}$ ls M→
Movies/ Music/  
{your computer name}:~ {your user name}$ ls M🁢
```

In this case there are two items that begin with M, so the command line lists them both, and retains the text that you started. Now add one more letter, `o` and press the `tab` key:

```
{your computer name}:~ {your user name}$ ls Movies/🁢
```

There was only one item that began with `Mo`, the Movies directory. If you press `return` you will see the contents of that folder.

Tab completion is very useful for file names that have spaces in them. For instance:

```
{your computer name}:~ {your user name}$ls -la Public/Drop Box
ls: Box: No such file or directory
ls: Public/Drop: No such file or directory
{your computer name}:~ {your user name}$ 🁢
```

Basically the `ls` program is confused by the space in name of the directory `Drop Box`, and it thinks you want to list the contents of `Drop` and `Box` as seperate arguments. 

You can fix this by putting quotes around the path and file name:

```
{your computer name}:~ {your user name}$ls -la "Public/Drop Box"
total 0
drwx-wx-wx+ 3 ChristopherA  staff  102 Oct 21 18:44 .
drwxr-xr-x+ 5 ChristopherA  staff  170 Oct 21 18:44 ..
-rw-r--r--  1 ChristopherA  staff    0 Oct 21 18:44 .localized
{your computer name}:~ {your user name}$ 🁢
```

Alternatively can fix this by "escaping" the space by putting a backslash in front it, for example:

```
{your computer name}:~ {your user name}$ls -la Public/Drop\ Box
total 0
drwx-wx-wx+ 3 ChristopherA  staff  102 Oct 21 18:44 .
drwxr-xr-x+ 5 ChristopherA  staff  170 Oct 21 18:44 ..
-rw-r--r--  1 ChristopherA  staff    0 Oct 21 18:44 .localized
{your computer name}:~ {your user name}$ 🁢
```

Finally, you just type type `ls -la Pu` then press tab, then type `D` and press tab again. The path will be auto-completed with all the spaces properly escaped.

Finder Path Trick
-----------------

One trick for very long paths with spaces and other special characters in them is that you can drag the file or folder from a Finder window (or the folder icon in the title bar of a Finder window) to the prompt, and the full path and file name will be appended to your command line.

Try `ls ` followed by dragging a random folder open in the Finder's GUI, then press `return`.

Absolute Paths and Home Directory
---------------------------------

So far, we have listed the contents of directories that exist inside our current directory. Every directory on your computer has a name and a path that takes you to it.

What if we want to see other directories? One way is by what is known as the "absolute path". These paths begin with the the `/` character.

Try it:

```
{your computer name}:~ {your user name}$ls /
Applications			home
Library				installer.failurerequests
System				net
Users				private
Volumes				sbin
bin				tmp
dev				usr
etc				var
{your computer name}:~ {your user name}$ 🁢
```

This reveals items in the "root" folder of your computer. Some you will recognize from the Finder GUI, others are invisible to the Finder. From the command-line, the root directory `/` is the starting point all the contents of your computer. It contains all the directories on your boot drive, directories for other drives, as well as a number of special system directories.

Now lets look at the absolute path for the Users Directory:

```
{your computer name}:~ {your user name}$ls /Users
{your user name} Shared
{your computer name}:~ {your user name}$ 🁢
```

Now lets add your user name (if it has a space in it try tab completion!):

```
{your computer name}:~ {your user name}$ls /Users/{your user name}
Desktop		Downloads	Movies		Pictures
Documents	Library		Music		  Public
{your computer name}:~ {your user name}$ 🁢
```

This is is your current working directory, which is also the default "home" directory that the shell application defaults to, so it gives same exact result as `ls` by itself. 

Your home directory `/Users/{your user name}/` or `~` for short, contains your personal files and directories. For example Pictures, Music, Documents, etc. Each of these directories is referenced as /home/{your user name}/{directory name}. For example Documents is located at /home/{your user name}/Documents.

This home path will be different for each user of the machine, so there is a shortcut for it that is different for each user, taking them to their home directory. This is the tilde character `~`. Thus `ls`, `ls /Users/{your user name}/` and 'ls ~` all give the same result.

Like with directories, files are referenced in the same way, for example a file named temp.txt located at the home directory of the user christophera can be referenced using the full path `/Users/christopher/temp.txt` or `~/temp.txt` by that user.

Both files and directories can be referenced using their absolute paths from everywhere in the system. Additionally one can access them using only their name if it is in the same directory. For example, if your current working directory is `~` when using the terminal, you can access `/Users/{your user name}/temp.txt` file by entering just `temp.txt`.

Changing Working Directory
--------------------------

In all of the examples above our current working directory path was the home directory. To change the current working directory, type `cd` followed by the {directory path}, for example:

```
{your computer name}:~ {your user name}$cd Desktop
{your computer name}:Desktop {your user name}$ 🁢
```

Note that your prompt now displays your working directory. To see the "absolute" path of that directory, type `pwd` again.

```
{your computer name}:Desktop {your user name}$ pwd
/Users/{your user name}/Desktop
{your computer name}:Desktop {your user name}$ 🁢
```

To return to your home directory, you can type `cd` with no options or arguments, but I prefer to type `cd ~` to remind me that I'm returning to home.

Creating a Temp Directory
-----------------------------

In most of remaining examples I'm no longer going to demonstrate the full prompt. Instead, when you see the first `$` it shows where you are to type to the right of that prompt. A final `$` with no text shows that the the output from your command has completed.

As we don't want to clutter our home directory with lots of files, lets create a `temp` directory to hold our future work. We will use the `mkdir` (_make directory_) command, then enter the folder with the `cd` command, and confirm that we are there with the `pwd' command.

```
$ cd ~
$ mkdir temp
$ cd temp
$ pwd
/Users/{your user name}/temp
$
```

Manipulating Files
------------------

To create your first empty file, use the `touch` command followed by the filename:

```
$ touch temp.txt
$
```

You can see that this file exists with the `ls` command:

```
$ ls
temp.txt
$
```

You can edit this text file with your Mac GUI text editor (by default the _Text Edit_ app in your _Applications_ folder) by using the `open` command.

```
$ open temp.txt
$
````

Enter some text in that file, save it (use `command + S`) and close it (use `command + W`). Then go back to terminal using either `command + tab` to cycle through your apps, or `command + space + term`. When using the Mac command-line it is important to learn these command keys — your hands should rarely need to leave the keyboard.

Now we can display that text using the `cat` command (whose name is short for _concatenate_).

```
$ cat temp.txt
The quick brown fox jumped over the lazy dog.
$
````

If there were many pages of text, you can also use the `more` command, which if there is more than window of text will display one window full at a time. Just type `space` to see the next window, or `q` to quit, or `h` to see a list of other choices.

Now we can copy that file using the `cp` (_copy_) command.

```
$ cp temp.txt temporary.txt
$ cat temporary.txt
The quick brown fox jumped over the lazy dog.
$ ls
temp.txt	temporary.txt
$
````

We can copy that file to another directory as well, by adding the path. In this case we will copy a temp file to the home directory.

```
$ cp temp.txt ~/temp.txt
$ ls ~/*.txt
temp.txt
$
````

We can rename a file using the `mv` (_move_) command.

```
$ mv temp.txt temp.bak
$ ls
temp.bak	temporary.txt
$
```

We can also move a file with the same command.

```
$ ls
temp.bak	temporary.txt
$ ls ~/*.txt
temp.txt
$ mv ~/temp.txt ./temp.txt
$ ls
temp.bak	temp.txt  temporary.txt
$ ls ~/*.txt
$
```


We can delete all these file using the `rm` command (short for _remove_). Since `rm` can be dangerous, I always recommend you use it with the option `-i` which makes it interactive.

```
$ rm -i temp.txt
remove temp.txt? y
$ rm -i temporary.txt
remove temporary.txt? y
$ rm -i temp.bak
remove temp.bak? y
$
````


The .. and . Relative Paths
---------------------------

There are two special paths, the `.` and '..` - these are are used for what are _relative_ paths.

The `..` directory is the directory _above_ the current working directory. So while still in the `~/temp` directory you type 'ls ..` and you will see the contents of the home directory:

```
$ ls ..
Desktop		Downloads	Movies		Pictures
Documents	Library		Music		Public
$
```

While in the ~/temp you can also enter `ls ..\{directory name}` to see sibling directories under the home directory.

If you were deep inside a complex set of directories, you can get out of them by entering `cd ..` - note how the prompt changes after each command:

```
{your computer name}:~ temp {your user name}$ pwd
/Users/ChristopherA/temp
{your computer name}:~ temp {your user name}$ cd ..
{your computer name}:~ {your user name}$ cd ..
{your computer name}:Users {your user name}$ cd ..
{your computer name}:/ {your user name}$ cd ~/temp
{your computer name}:temp {your user name}$ pwd
/Users/{your user name}/temp
{your computer name}:~ {your user name}$ 
```

A path beginning with `.`  means relative to the current working directory. In effect `ls .` is the same as `ls`. There are times when you absolutely want a path to be relative to where you are currently, use the `.` form.

The * and ? Wildcards
---------------------

Sometimes you want copy, rename or delete multiple files all at once. We can do this by using the `*` (sometimes called  _star_) wildcard character to replace zero or more characters in a filename or directory.

The command `rm *` will delete every thing in the current working directory except for those files that are special and begin with a `.`, thus until you are very experienced, I recommend that you always use the `-i` (for _interactive_) option when using `rm`.

Try this experiment:

```
$ cd ~/temp
$ ls
$ ls -a
.	..
$ mkdir there
$ touch .where here that then
$ ls
here	that	then	there
$ ls -a
.	..	.where	here	that	then	there
$ rm -i t*
remove that? y
remove then? y
rm: there: is a directory
$ ls
here there
$ ls -a
.	..	.where	here there
$ rm -i *
remove here? y
rm: there: is a directory
$ ls
there
$ ls -a
.	..	.where	there
$ rm -i .w*
remove .where? y
$ rm -i .*
rm: "." and ".." may not be removed
$
```
As you can see, trying to remove directories, including the `.` (the current directory) and `..` (the parent directory) is not allowed with the `rm -i` command. So how do you delete directories? With the `rmdir` command.

```
$ ls
there
$ rmdir there
$ ls
$
```

This command may seem dangerous, but the `rmdir` command has a failsafe that doesn't allow you to delete folders that have contents. First you must delete any contents.

```
$ mkdir there
$ touch there/that
$ ls there
that
A$ rmdir there
rmdir: there: Directory not empty
$ rm -i there/*
remove there/that? y
$ rmdir there
$ ls
$
```

A particularly common use of the `*` wildcard is to view or delete only files with certain extensions. For instance:

```
$ touch a.txt b.txt a.jpg b.jpg
$ ls a*
a.jpg	a.txt
$ ls a.*
a.jpg	a.txt
$ ls *.txt
a.txt	b.txt
$ rm -i a.*
remove a.jpg? y
remove a.txt? y
$ ls
b.jpg	b.txt
$ rm -i *.txt
remove b.txt? y
$ ls
b.jpg
$ rm -i *.*
remove b.jpg? y
$ ls
$
```

Suppose you have some files ending in `.jpg` and some ending in `.jpeg` -- the asterisk wildcard makes clean-up easy:

```
$ touch a.jpg b.jpeg c.java d.js
$ rm -i *.jp*g
remove a.jpg? y
remove b.jpeg? y
$ rm -i *.j*
remove c.java? y
remove d.js? y
$ ls
$
```

The `*` wildcard match zero or more characters, but sometimes you may want to match only one character. In this case we use the `?` wildcard:

```
$ touch task  taskA  taskB  taskXY
$ ls task*
task  taskA  taskB  taskXY
$ ls task?
taskA  taskB
$ ls task??
taskXY
$ rm -i ?ask*
remove task? y
remove taskA? y
remove taskB? y
remove taskXY? y
$ ls
$
```

So now that we are done with our temp directory, we can delete the entire directory and all of its contents at once with the `rm -ir` command and option:

```
$ cd ..
$ pwd
/Users/{your user name}
$ ls temp
task  taskA taskB taskXY
$ rm -ir temp
examine files in directory temp? y
remove temp/task? y
remove temp/taskA? y
remove temp/taskB? y
remove temp/taskXY? y
remove temp? y
$
```

Getting Help
------------

Every one of these commands have help files associated with them, which can be viewed with the `man` (short for _manual_) command.

Like the `more` command, typing `space` moves down a window full of text, and typing `q` will quit. You can even see the man page for man with `man man`.

Many, but not all commands will give you a brief summary of what they do if you type them without any options, or with the option `-h` or `--help`. Many options may be cryptic, but the man page for the commands should explain them in more detail.

















