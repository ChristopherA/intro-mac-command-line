Command Line Basics
===================

What is a Command Line Interface?
---------------------------------
Underneath the wonderful Mac Graphical User Interface ("GUI") is a powerful and flexible method of working directly with files and the web. This is known as the "command line interface", or sometimes CLI.

It may seem geeky at first, and at first its depth may seem intimidating, but you don't need to learn it all of it for it for the command line to become quite useful to you. In particular, in order to learn how to program web applications or clients on the Mac, you will need to have some comfort with basics of the Mac command line.

The Terminal
------------
First, you should learn how to start the built-in application that runs the Mac CLI, called the _Terminal_. To open it, rather than the usual GUI method of opening the Applications/Utilities directory and double-clicking the Terminal app, instead you should learn to open the Terminal with your keyboard.

Type `command + spacebar` and then type `terminal` and press return. In fact, you don't even need to typically type the whole word — just the first few letters `ter` or `term` is usually enough.

When Terminal first opens, you should see a small window with this text in it:

```
Last login: {some date} on console
{your computer name}:~ {your user name}$ 🁢
```
The window you see is created by the _Terminal_ application, but the text you see is is created by 'shell' application (the Mac defaults to shell known as _bash_). They are two different programs, and often words command line, terminal, shell, or bash are used interchangably, but they are all slightly different things. Someday you may want to switch to a more sophisticated Terminal applications (_iTerm_ is popular), or switch to a more sophisted text shell (_tsch_ is popular), or both. For the purpose of this _Intro to the Command Line_ tutorial we will only be using the default Mac _Terminal_ app, and the _bash_ command line text shell.

The text before and including the $ is known as the _prompt_. The 🁢 symbol is the location of your _text cursor_. Anything you type will appear under the text cursor and the text cursor will move to the next spot.

Looking at Directories
----------------------

If you now type `pwd` you will see the text appear to the right of the $. This is your _command_. Type return to _execute_ your command.

```
{your computer name}:~ {your user name}$ pwd
/Users/{your user name}
{your computer name}:~ {your user name}$ 🁢
```

The command `pwd` is short for 'print working directory' which basically means "Where am I now?". The result of `pwd` is the _path_ to where any shell commands will default to.

Whenever you first open the Terminal, it will open with your working directory (aka folder) starting at your _home_ directory. Your home directory on the Mac will almost always be /Users/{your user name}, the directory that contains your Desktop, Documents, Downloads, Movies, Music, Pictures and Public directories. To see this list, enter the `ls` command (short for 'list'):

```
{your computer name}:~ {your user name}$ ls
Desktop		Downloads	Movies		Pictures
Documents	Library		Music		Public
{your computer name}:~ {your user name}$ 🁢
```

Notice that the `ls` command showed us one additional directory that you can't see from your Mac's Finder GUI: the Library directory. There are other invisible files. We can see these by adding to the `ls` command what is known as a parameter, in this case `-a`.  Together the command and parameter `ls -a` means 'list all'.

```
{your computer name}:~ {your user name}$ ls
.			Desktop			Movies
..			Documents		Music
.CFUserTextEncoding	Downloads		Pictures
.Trash			Library			Public
{your computer name}:~ {your user name}$ 🁢
```

The 'ls -a' command reveals a number of files that are invisible to the Finder and the Mac GUI. Any file that begins with a period will be invisible to the Finder. We will learn more about these files later.

To look at the contents of another directory, you can add a _path_ parameter to the `ls` command. Type `ls Public` to see the contents of your Public directory (the name of the directory `Public` is case sensitive — `public` will not work).

```
{your computer name}:~ {your user name}$ ls Public
Drop Box
{your computer name}:~ {your user name}$ 🁢
```

The `ls -l` command lists additional information about each item in the current directory:

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

You can combine parameters, so `ls -la` will list all the information about all the contents of the current directory, including hidden dot `.` files and invisible directories like the `Library`.

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
drwxr-xr-x   2 {your user name}  staff    68 Apr 12 00:11 Projects
drwxr-xr-x+  5 {your user name}  staff   170 Oct 21 18:44 Public
{your computer name}:~ {your user name}$ 🁢
```

The `d` on the left tells you that the item in the directory is another directory. A hyphen `-` tells you that the item is a file.

You can also add the path to see the contents of that `ls -la Public`

```
{your computer name}:~ {your user name}$ ls Public
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

A useful feature that the command line offers is called "command line completion" or "tab completion". What this means if you enter insufficient information, you can press the `tab` key to see what the choices are, or if there is only one choice, select that one.

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

Basically the shell application is confused by the space in name of the directory `Drop Box`. You can fix this by "escaping" the space by putting a backslash in front it, for example:

```
{your computer name}:~ {your user name}$ls -la Public/Drop\ Box
total 0
drwx-wx-wx+ 3 ChristopherA  staff  102 Oct 21 18:44 .
drwxr-xr-x+ 5 ChristopherA  staff  170 Oct 21 18:44 ..
-rw-r--r--  1 ChristopherA  staff    0 Oct 21 18:44 .localized
{your computer name}:~ {your user name}$ 🁢
```

Or you just type type `ls -la Pu` then press tab, then type `D` and press tab again. The path will be auto-completed.

Absolute Paths and Home Directory
---------------------------------

So far, we have listed the contents of directories that exist inside our current directory. What if we want to see other directories? One way is by what is known as the "absolute path". These paths begin with the the `/` character. Try it:

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

This reveals items in the "root" folder of your computer. Some you will recognize from the Finder GUI, others are invisible to the finder. Now lets look at the absolute path for the Users Directory:

```
{your computer name}:~ {your user name}$ls /Users
{your user name} Shared
{your computer name}:~ {your user name}$ 🁢
```

Now lets add your user name (if it has a space in it try tab completion!):

```
{your computer name}:~ {your user name}$ls /Users/{your user name}
Desktop		Downloads	Movies		Pictures	Public
Documents	Library		Music		Projects
{your computer name}:~ {your user name}$ 🁢
```

This is is your current working directory, which is also the default "home" directory that the shell application defaults to, so it gives same exact result as `ls` by itself.

This home path will be different for each user of the machine, so there is a shortcut for it that is different for each user, taking them to their home directory. This is the tilde character `~`. Thus `ls`, `ls /Users/{your user name}/` and 'ls ~` all give the same result.

Changing Working Directory
--------------------------



