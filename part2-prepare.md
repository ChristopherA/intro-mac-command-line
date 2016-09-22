Part 2 - Preparation and Installation
=====================================

Every Mac supports a large numer of command line tools, however, not every program that you need for web development is included by default. This tutorial instructs you on how to prepare and configure your Mac to make it a powerful web development system.

You do not need to deeply understand all the commands that are used here — they are explained briefly, but you do not lean to learn them yet. I am explaining only because it is YOUR computer and you should know what and why these tools have been added.

System Updates
--------------

The first thing you need to do is to make sure that you have the most recent version of the OS, which as of the writing of this intro is Mac OS X Yosemite 10.10.3. Everything in these introduction files should work on previous version of the the OS, however, when you are doing web development it is important to have the most recent updates for security reasons.

You can get all your system updates by going the the _App Store…_ item under the Apple Menu, clicking on the _Updates_ tab and pressing the _Update All_ button. However, you can also do it from the command line.

The `sudo` command is used to run programs that need additional privileges to change your computer, and thus your Mac's administrative password. `/usr/sbin/softwareupdate -l` is the program that checks with Apple's update servers for the most recent version. You may need to execute this command multiple times, or even reboot your system if your Mac is not current.

```
$ cd ~
$ sudo /usr/sbin/softwareupdate -l

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
Software Update Tool
Copyright 2002-2012 Apple Inc.

Finding available software
No new software available.
$
```

Install Apple's Command Line Tools
----------------------------------

Next we are going to install Apple's Command Line Tools, which will install a number of development tools that will be available from the command line. There is a "trick" of touching a file that makes this happen from the command line without loading Apple's XCODE development environment for creating Mac and iOS apps.

Because you've recently entered an administrative password for the `sudo` command, the shell may not ask you for your admin password again.

```
$ touch /tmp/.com.apple.dt.CommandLineTools.installondemand.in-progress
sudo /usr/sbin/softwareupdate -ia
Software Update Tool
Copyright 2002-2012 Apple Inc.

Finding available software

Downloading Command Line Tools (OS X 10.10)
Downloaded Command Line Tools (OS X 10.10)
Installing Command Line Tools (OS X 10.10)
Done with Command Line Tools (OS X 10.10)
Done.
$/bin/rm /tmp/.com.apple.dt.CommandLineTools.installondemand.in-progress
```

With this installation you have just installed 92 development tools into your /Library/Developer/CommandLineTools/bin/

```
BuildStrings CpMac DeRez GetFileInfo MergePef MvMac ResMerger Rez RezDet RezWack SetFile SplitForks UnRezWack ar as asa bison c++ c89 c99 cc clang clang++ cmpdylib codesign_allocate cpp ctags ctf_insert dsymutil dwarfdump dyldinfo flex flex++ g++ gatherheaderdoc gcc gcov git git-cvsserver git-receive-pack git-shell git-upload-archive git-upload-pack gm4 gnumake gperf hdxml2manxml headerdoc2html indent install_name_tool ld lex libtool lipo lldb llvm-cov llvm-profdata lorder m4 make mig mkdep nasm ndisasm nm nmedit otool pagestuff projectInfo ranlib rebase redo_prebinding resolveLinks rpcgen segedit size strings strip svn svnadmin svndumpfilter svnlook svnrdump svnserve svnsync svnversion unifdef unifdefall unwinddump what xml2man yacc
```

From now on, the Mac App Store's regular System Update will keep these tools current.

Create Some Additional Folders in Home
--------------------------------------

I find it useful to prepare in advance some additional folder in my home "~" directory. The convention I use is that if the folder starts with a Capital, the folder contains items for Finder's GUI. If the folder begins with a lower-case letter (making it faster to type) then it is to used by the CLI.

All of these folders are optional — many you will not use until much later in this tutorial:

* ~/.dotfiles # This is where I backup my dotfiles (explained later) and store some other useful tools.
* ~/.dotfiles/bin # This is where I keep small command line scripts that I use regularly.
* ~/Applications # This is where I keep any GUI apps that are installed for development purposes seperate from those root /Applications folder.
* ~/code # This is where store the source code from open source repositories from github
* ~/Pool # This is where I store large files that I exclude from backing up on Time Machine. Great for movies, large installer files, etc. that I have backuped up elsewhere or are easily downloaded again from the net.
* ~/projects # This is where I keep repositories of my own source code or others work-in-progress.
* ~/temp # This is where I keep code and projects that are just temporary and can be deleted at any time. I practice here.

```
$ mkdir ~/.dotfiles ~/.dotfiles/bin ~/Applications ~/code ~/Pool ~/projects ~/temp
$ ls -a
.			Desktop			Pictures
..			Documents		Pool
.CFUserTextEncoding	Downloads		Public
.Trash			Library			code
.dotfiles		Movies			projects
Applications		Music			temp

$
```

Installing Brew
---------------

Next we are going to install [Homebrew](http://brew.sh) (known as `brew` for short), a software package manager.

You can consider `brew` to be an app store for open source web apps and developer tools. There are thousands of different open source code bases, all with various dependences on each other, and each requiring different configurations for what kind of computer OS it is running on (Linux, Unix, Mac, Windows, etc.). Brew manages those complexities. If request to install a particular tool it that needs other packages, tools or libraries to run, Brew will first install them in the correct order. Brew also stores its files in some specific ways that are best practices so that different tools don't interfere with each other.

Brew is not installed on your Mac by default, so you'll need to run a script to install it. They provide a script to install it on their github site, which is run by `ruby` which is installed on your Mac by default. WARNING: Be cautious whenever someone asks you to run a script that has `curl` command in it, because if the author is malicious they can corrupt your system or make it vulnerable. In this case the script is run from a trusted website (github), and is from a trusted account there (Homebrew). I suggest you go to the [Homebrew](http://brew.sh) website and confirm that this is the correct script to use.

This script will ask you for your administrator password.

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
==> This script will install:
/usr/local/bin/brew
/usr/local/Library/...
/usr/local/share/man/man1/brew.1

Press RETURN to continue or any other key to abort
==> /usr/bin/sudo /bin/mkdir /usr/local
Password:
==> /usr/bin/sudo /bin/chmod g+rwx /usr/local
==> /usr/bin/sudo /usr/bin/chgrp admin /usr/local
==> /usr/bin/sudo /bin/mkdir /Library/Caches/Homebrew
==> /usr/bin/sudo /bin/chmod g+rwx /Library/Caches/Homebrew
==> Downloading and installing Homebrew...
remote: Counting objects: 3528, done.
remote: Compressing objects: 100% (3382/3382), done.
remote: Total 3528 (delta 34), reused 1561 (delta 18), pack-reused 0
Receiving objects: 100% (3528/3528), 2.65 MiB | 3.78 MiB/s, done.
Resolving deltas: 100% (34/34), done.
From https://github.com/Homebrew/homebrew
 * [new branch]      master     -> origin/master
HEAD is now at f1964ec ngircd: update 22.1 bottle.
==> Installation successful!
==> Next steps
Run `brew help` to get started
$
```

After installing Homebrew, the first thing we want to do is confirm that it has been installed correctly, or if there has been something else installed on your Mac previously that will cause problems.

```
$ brew doctor
Your system is ready to brew.
$
```

If there were any errors, `brew doctor` will tell you how to fix them. If what it suggests to fix the problem doesn't work, I find that almost every problem that has come up is a question on the website [StackOverflow](http://stackoverflow.com) so search for your solution there.

Install Git
-----------

The first command line application we will install is [Git](http://git-scm.com), which is the most popular source code version control system. A source code control system helps you manage the production of your code, backup and restore different versions of your code, and work cooperatively with others. `git` is popular because it is open source, it is distributed (i.e. there isn't one master repository the files have to come from), works with projects as large as the Linux operating system with thousands of contributors, small team projects, and yet is useful for even for a single programmer.

We will use `brew` to install git, so always before we brew anything we want to make sure that `brew` is current. We just installed it so we don't really need to do this now, but I will demonstrate best practices (everything after a # is a comment):

```
$ brew doctor # run self test to see if brew is running properly
Your system is ready to brew.
$ brew update # update brew itself to the latest version, and get latest list of apps
Already up-to-date.
$ brew upgrade # upgrade any apps managed by brew to the most recent version
$
```

Next we wil confirm information about git, then we install it.

```
$ brew info git
git: stable 2.3.5 (bottled), HEAD
http://git-scm.com
/usr/local/Cellar/git/2.3.5 (1363 files, 31M) *
Not installed
From: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/git.rb
$ brew install git
==> Downloading https://homebrew.bintray.com/bottles/git-2.3.5.yosemite.bottle.t
######################################################################## 100.0%
==> Pouring git-2.3.5.yosemite.bottle.tar.gz
==> Caveats
The OS X keychain credential helper has been installed to:
  /usr/local/bin/git-credential-osxkeychain

The "contrib" directory has been installed to:
  /usr/local/share/git-core/contrib

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completion has been installed to:
  /usr/local/share/zsh/site-functions
==> Summary
🍺  /usr/local/Cellar/git/2.3.5: 1363 files, 31M
$ git --version
git version 2.3.5
$
```

Install Cask
------------

[Cask](http://caskroom.io) is a special brew application that installs a number of Mac GUI apps. I find it particularly useful for installing those developer apps require an installer or a .dmg file. One other useful thing that it does is that it puts the app into your ~/Applications folder, keeping them seperate from your other apps.

```
$ brew install caskroom/cask/brew-cask
==> Tapping caskroom/cask
Cloning into '/usr/local/Library/Taps/caskroom/homebrew-cask'...
remote: Counting objects: 134040, done.
remote: Compressing objects: 100% (31/31), done.
remote: Total 134040 (delta 14), reused 0 (delta 0), pack-reused 134009
Receiving objects: 100% (134040/134040), 39.94 MiB | 6.73 MiB/s, done.
Resolving deltas: 100% (88744/88744), done.
Checking connectivity... done.
Tapped 1 formula (2823 files, 60M)
==> Installing brew-cask from caskroom/homebrew-cask
==> Cloning https://github.com/caskroom/homebrew-cask.git
Cloning into '/Library/Caches/Homebrew/brew-cask--git'...
remote: Counting objects: 2686, done.
remote: Compressing objects: 100% (2531/2531), done.
remote: Total 2686 (delta 198), reused 659 (delta 139), pack-reused 0
Receiving objects: 100% (2686/2686), 5.62 MiB | 6.11 MiB/s, done.
Resolving deltas: 100% (198/198), done.
Checking connectivity... done.
Note: checking out 'e65c40bb2bb02d7aa26f3d0ed6217862f2436055'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

==> Checking out tag v0.53.3
🍺  /usr/local/Cellar/brew-cask/0.53.3: 2421 files, 9.5M, built in 6 seconds
$
```

Installing the Atom Text Editor
-------------------------------

Next we are going to use `brew cask` to install the Atom text editor. There are many powerful command line text editors out there (and a constant battle between fans of emacs vs those for vim), but learning them is outside the scope of this tutorial. In the meantime there is a very powerful, free and open source GUI text editor optimized for command line and web developers called Atom. One of its best features is its integration with Git.

We will install it with `brew cask`

```
$ brew cask install atom
==> We need to make Caskroom for the first time at /opt/homebrew-cask/Caskroom
==> We'll set permissions properly so we won't need sudo in the future
Password:
chmod: /opt: No such file or directory
==> Downloading https://atom.io/download/mac
######################################################################## 100.0%
==> Symlinking App 'Atom.app' to '/Users/ChristopherA/Applications/Atom.app'
==> Symlinking Binary 'apm' to '/usr/local/bin/apm'
==> Symlinking Binary 'atom.sh' to '/usr/local/bin/atom'
🍺  atom staged at '/opt/homebrew-cask/Caskroom/atom/latest' (11288 files, 239M)
$
```

From now own instead of using the `open` command to edit a text file, we will use `atom`, for example:

```
$ touch ~/temp/temp.txt
$ atom ~/temp/temp.txt
```
You can now edit this file using the familar Mac GUI experience.

Install Node
------------

[Node](https://nodejs.org) is a popular web server tool that runs Javascript. Installed on the Mac, it also provides an interactive environment for learning how to Javascript code and use various frameworks. We are installing it because a number of tutorials later use it.

```
$ brew install node
==> Downloading https://homebrew.bintray.com/bottles/node-0.12.2_1.yosemite.bott
######################################################################## 100.0%
==> Pouring node-0.12.2_1.yosemite.bottle.tar.gz
==> Caveats
If you update npm itself, do NOT use the npm update command.
The upstream-recommended way to update npm is:
  npm install -g npm@latest

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/node/0.12.2_1: 2603 files, 28M
$
```

Web Get
-------

I find the `wget` tool to be very useful. Point it to a URL and it downloads the contents to a file. You can also do this with the built-in `curl` tool, but I find `wget` very useful at time.

```
$ brew install wget
==> Installing wget dependency: openssl
==> Downloading https://homebrew.bintray.com/bottles/openssl-1.0.2a-1.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring openssl-1.0.2a-1.yosemite.bottle.tar.gz
==> Caveats
A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
  /usr/local/etc/openssl/certs

and run
  /usr/local/opt/openssl/bin/c_rehash

This formula is keg-only, which means it was not symlinked into /usr/local.

Mac OS X already provides this software and installing another version in
parallel can cause all kinds of trouble.

Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

    LDFLAGS:  -L/usr/local/opt/openssl/lib
    CPPFLAGS: -I/usr/local/opt/openssl/include

==> Downloading https://www.geotrust.com/resources/root_certificates/certificates/Equifax_Secure_
######################################################################## 100.0%
==> /usr/local/Cellar/openssl/1.0.2a-1/bin/c_rehash
==> Summary
🍺  /usr/local/Cellar/openssl/1.0.2a-1: 463 files, 18M
==> Installing wget
==> Downloading https://homebrew.bintray.com/bottles/wget-1.16.3.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring wget-1.16.3.yosemite.bottle.tar.gz
🍺  /usr/local/Cellar/wget/1.16.3: 9 files, 1.5M
Aeguss-MacBook-Pro:intro-mac-command-line ChristopherA$
```

Brew & Cask Cleanup
-------------------

Ater we `brew` or `brew cask` anything it is best practices to tell brew to cleanup. You don't have to do this after each item brew, you can brew a number of items at once and only cleanup after.

```
$ brew linkapps --local
Finished linking. Find the links under /Users/ChristopherA/Applications.
$ brew cleanup
$ brew prune
Pruned 0 dead formulae
$ brew cask cleanup
brew cask cleanup
==> Removing dead symlinks
Nothing to do
==> Removing cached downloads
/Library/Caches/Homebrew/atom-latest
/Library/Caches/Homebrew/Casks/atom-latest
$
```

Final Cleanup
-------------

The locate and whathis databases, used by the command line utilities `locate`, `whatis` and `apropos`, are only generated weekly, so run this after adding any commands to update the database. This will happen in the background and can take some time to generate the first time.

```
$ sudo periodic daily weekly monthly
```
