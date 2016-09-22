Part 3 - Customize Your Environment
===================================

This part is entirely optional. In it I have a number of recommendations as to how to customize your command line "environment" so that it will be a little easier to use. There is nothing here that is required for later on.


Solarized Terminal Profiles
---------------------------

The _Terminal_ app allows you to choose from a number of options for how the terminal window is displayed. Open it's _Terminal_ menu _Preferences_ submenu and a number of options can be defined. Click on the _Profiles_ tab and see the choices. Of the default options, the _Homebrew_ profile is a useful choice — it is bright text on dark, which I personally find easier for coding.

I personally use a dark background, but with a more subtly colored text based on the [Solarized](http://ethanschoonover.com/solarized). You can download and open my preferences using the `wget` command.

```
$ cd ~/temp
$ wget https://github.com/ChristopherA/dotfiles/blob/master/install/osxterminal/christophera-dark.terminal
$ open christophera-dark.terminal
$ rm christophera-dark.terminal
```

In the _Terminal_'s _Preferences_, in the _General_ pane, set the "On startup open: New window with profile" and then select 'christophera-dark'

You can set Atom's theme to use the a similar set of dark solarized colors. The theme is called _Solarized Dark_ and it comes installed by default with Atom and can be activated by going to the Themes section in the Settings view `command + -`) and selecting it from the Syntax Themes dropdown menu.

CLI Colors
==========

You can enable syntax colors for how various commands output text the command line. To see this, try this:

```
$ export CLICOLOR=1
```

Now type `ls -la` and you will see that directories and files are listed with different colors.

For compatibility with the solarized terminal theme, I also set some specific colors that I find blend well:

```
$ export LSCOLORS=gxfxbEaEBxxEhEhBaDaCaD
$ export LS_COLORS="di=36;40:ln=35;40:so=31;:pi=0;:ex=1;;40:bd=0;:cd=37;:su=37;:sg=0;:tw=0;:ow=0;:"
```

Now if you want these colors to be displayed ever time you open _Terminal_, you'll need to add them to a special file so that they will be always loaded. This file is called is `~/.bash_profile`.

```
$ atom ~/.bash_profile
```

Add all three lines (with out the $), save, quit _Terminal_ and launch it again, and you'll see all your color settings as you prefer.

There is a `brew` app called `grc` (for [Generic Colourizer](http://kassiopeia.juls.savba.sk/~garabik/software/grc.html)) that adds colorization to a lot more commands than the above does.

```
$ brew install grc
==> Downloading http://korpus.juls.savba.sk/~garabik/software/grc/grc_1.9.orig.tar.gz
######################################################################## 100.0%
==> Caveats
New shell sessions will start using GRC after you add this to your profile:
  source "`brew --prefix`/etc/grc.bashrc"
==> Summary
🍺  /usr/local/Cellar/grc/1.9: 32 files, 148K, built in 3 seconds
$
```

Like with CLI colors, you'll need to add a line to your to your `~/.bash_profile`. I recommend a slightly different syntax than what `brew` suggests:

```
if [ -f $(brew --prefix)/etc/grc.bashrc ]; then
  . $(brew --prefix)/etc/grc.bashrc
fi
```

Bash Completion
---------------

There are a number of apps that don't allow tab completion of partial text the way others do. the `brew` app called `bash-completion` (from http://bash-completion.alioth.debian.org) will make many more commands support tab completion.

```
$ brew install bash-completion
==> Downloading http://bash-completion.alioth.debian.org/files/bash-completion-1.3.tar.bz2
######################################################################## 100.0%
==> Patching
patching file bash_completion
==> ./configure --prefix=/usr/local/Cellar/bash-completion/1.3
==> make install
==> Caveats
Add the following lines to your ~/.bash_profile:
  if [ -f $(brew --prefix)/etc/bash_completion ]; then
    . $(brew --prefix)/etc/bash_completion
  fi

Homebrew's own bash completion script has been installed to
  /usr/local/etc/bash_completion.d

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/bash-completion/1.3: 188 files, 1.1M, built in 20 seconds
$
```

To install bash-completeion one time type `. $(brew --prefix)/etc/bash_completion`. You can see all the apps that this `brew` recipe adds by typing 'complete -p'

Once again, if you want this permanently, is are some more lines to add to your ~/.bash_profile

```
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

Better Prompt
-------------

You can customize the shell prompt (the part before $) in quite a few ways, but I find the `brew` recipe called `bash-git-prompt` to be quite powerful, especially once you start using `git`.

```
$ brew install bash-git-prompt
==> Downloading https://github.com/magicmonty/bash-git-prompt/archive/2.3.5.tar.gz
######################################################################## 100.0%
==> Caveats
You should add the following to your .bashrc (or equivalent):
  if [ -f "$(brew --prefix bash-git-prompt)/share/gitprompt.sh" ]; then
    GIT_PROMPT_THEME=Default
    source "$(brew --prefix bash-git-prompt)/share/gitprompt.sh"
  fi
==> Summary
🍺  /usr/local/Cellar/bash-git-prompt/2.3.5: 21 files, 120K, built in 2 seconds
$
```

To run it one time, type:

```
GIT_PROMPT_THEME=Default
source "$(brew --prefix bash-git-prompt)/share/gitprompt.sh"
```

If you like it, add this to your ~/.bash_profile:

```
if [ -f "$(brew --prefix bash-git-prompt)/share/gitprompt.sh" ]; then
  GIT_PROMPT_THEME=Solarized
  source "$(brew --prefix bash-git-prompt)/share/gitprompt.sh"
fi
```

More Git & Github Tools
-----------------

You will be using `git` and the _GitHub_ serve regularly, so these tools add additional functionality.

The first is called `hub`, and it provides all the functionality of `git`, but adds some _GitHub_ specific features.

```
$ brew install hub


```

Since `hub` is compatible with `git`, I `alias` it in my `~/bash_profile`

```
alias git=hub
```

The `brew` recipe [git-extras]( https://github.com/visionmedia/git-extras) adds a number of additional useful `git` commands, and they are compatible with `hub`:

```
$ brew install git-extras
==> Downloading https://homebrew.bintray.com/bottles/git-extras-2.2.0.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring git-extras-2.2.0.yosemite.bottle.tar.gz
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/git-extras/2.2.0: 91 files, 388K
$
```

Finally, GitHub offers a useful Mac GUI app called [GitHub](https://mac.github.com) for browsing git repositories.

```
$ brew cask install github-desktop 
```
