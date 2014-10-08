---
layout: post
title: "Dotfiles and Bash History"
date: 2014-03-28 10:00:00
---

Using `Ctrl + P` or the up arrow is a handy way to recall recent commands in bash.

Like many command line features, bash's history tracking can be configured in its main dotfile, `.bashrc`.


# Dotfiles
Dotfiles are just plain text files that applications read for configuration whenever they are run.

Windows uses a "Registry" instead, which is much more structured but way more of a hassle to modify.

By default, dotfiles are hidden from directory listing commands such as `ls`.
You can run `ls -a` to have it display **all** files, even "hidden" ones
like dotfiles.

Dotfiles that affect general program configuration (as opposed to folder-specific configuration) are
conventionally placed in your home directory, which is `/Users/username` on OS X and
`/home/username` on Linux.


# HISTIGNORE and HISTCONTROL
`HISTIGNORE` and `HISTCONTROL` are two environment variable which bash uses
to change the behavior of its history tracking.

`HISTIGNORE` is a `:`-separated list of command patterns that bash should avoid saving
in its history file. For example:

{% highlight bash %}
export HISTIGNORE="ls:man"
{% endhighlight %}

would ignore all `ls` and `man` commands.

To disable `HISTIGNORE`, you can simply delete the entire `export HISTIGNORE=...` line
from your `.bashrc`.

`HISTCONTROL` is mostly used for ignoring duplicate entries and ignoring commands that start with
a space. You can have it ignore both by putting...

{% highlight bash %}
export HISTCONTROL="ignoreboth"
{% endhighlight %}

in your `.bashrc`. You can add these lines anywhere in the file.


# Reloading bash configuration without restarting your shell
If you're playing around with your configuration, it can get really annoying to keep restarting your shell.

Instead of quitting and re-opening it every time you modify your dotfiles, you can tell bash to read them again:

{% highlight bash %}
source ~/.bashrc
{% endhighlight %}

This will trigger bash to read your `.bashrc` again and run your changes without having to quit and reload!

