Command Line Basics
===================

What is a Command Line Interface?
---------------------------------
Underneath the wonderful Mac Graphical User Interface ("GUI") is a powerful and flexible method of working directly with files and the web. This is known as the "command line interface", or sometimes CLI.

It may seem geeky at first, and at first its depth may seem intimidating, but you don't need to learn it all of it for it for the command line to become quite useful to you. In particular, in order to learn how to program web applications or clients on the Mac, you will need to have some comfort with basics of the Mac command line.

The Terminal
------------
First, you should learn how to load the built-in application that runs the Mac CLI, called the "Terminal". To open it, rather than the usual GUI method of opening the Applications/Utilities folder and double-clicking the Terminal app, instead you should learn to open the Terminal with your keyboard.

Type `command + spacebar` and then type `terminal` and press return. In fact, you don't even need to typically type the whole word — just the first few letters `ter` or `term` is usually enough.

When Terminal first opens, you should see a small window with this text in it:

```
Last login: {some date} on console
{your computer name}:~ {your user name}$ 🁢
```

The text before and including the $ is known as the _prompt_. The 🁢 symbol is the location of your _text cursor_. Anything you type will appear under the text cursor and the text cursor will move to the next spot.

If you now type `pwd` you will see the text appear to the right of the $. This is your _command_. Type return to _execute_ your command.

```
{your computer name}:~ {your user name}$ pwd
/Users/{your user name}
{your computer name}:~ {your user name}$ 🁢
```

The command `pwd` is short for 'print working directory' which basically means "Where am I now?"

Whenever you first open the Terminal, it will open with your working directory (aka folder) starting at your _home_ directory. Your home directory on the Mac will almost always be /Users/{your user name}, the folder that contains your Desktop, Documents, Downloads, Movies, Music, Pictures and Public folders. To see this list, enter the `ls` command (short for 'list'):

```
{your computer name}:~ {your user name}$ ls
Desktop		Downloads	Movies		Pictures
Documents	Library		Music		Public
{your computer name}:~ {your user name}$ 🁢
```

Notice that the `ls` command showed us one directory that you can't see from the Mac GUI, the Library folder. There are other invisible files. We can see these by adding to the `ls` command what is known as a parameter `-a`.  Together the command and parameter `ls -a` means 'list all'.

```
{your computer name}:~ {your user name}$ ls
.			Desktop			Movies
..			Documents		Music
.CFUserTextEncoding	Downloads		Pictures
.Trash			Library			Public
{your computer name}:~ {your user name}$ 🁢
```



