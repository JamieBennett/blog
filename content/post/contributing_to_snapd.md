+++
Categories = ["Development","Linux"]
Description = "Contributing to snapd development"
Tags = ["Development","Linux","Snappy","snapd"]
date = "2016-06-01T09:40:26+01:00"
menu = "main"
title = "Contributing to the snapd project"
image = "/media/desktop.png"

+++
<img align=“center” src="/media/desktop.png">

There is a lot of buzz around snaps, the new packaging format created by Canonical to enable secure, transactional, and robust application updates, and rightly so. This new method of distributing applications is revolutionizing not only software on IoT devices, but on the desktop, server, and beyond. The software that actually runs the snap applications is called <code>snapd</code>. Hosted on [GitHub](https://github.com/snapcore/snapd), <code>snapd</code> uses the [Go language](https://golang.org) and is actively developed by a core set of developers, but, like most projects at Canonical, we actively encourage as much community participation as possible. One of the core developers, Zygmunt, posted a great outline on [how to make your first contribution to snapd](http://www.zygoon.pl/2016/06/making-your-first-contribution-to-snapd.html) and, taking up the challenge, I did exactly that.

Zygmunt's instructions are pretty clear but I thought I would look at this from a new developer's perspective, using a clean Ubuntu 16.04 install and with a new GitHub account. What follows is a guide to setting everything up ready for your first contribution. As a side note I have various machines I work on regularly, mainly my Lenovo laptop running Ubuntu, but also my Macbook Pro, and a HP Windows all-in-one. This allows me to look at the various platforms available to developers all of which are valid options for software development, especially in the IoT world.

## Installing Ubuntu 16.04
Installing Ubuntu is very straight-forward and, depending on the way you intend to run it, the instructions vary ever-so-slightly. There is a comprehensive guide to installing Ubuntu as the only OS available on the [Ubuntu Site](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) which will get you up and running in no time. Remember to download Ubuntu 16.04. On the Mac and Windows platform you will need to install Ubuntu as a Virtual Machine (VM) but again, this is straight-forward. I chose to use [VirtualBox](https://www.virtualbox.org) as it is free, feature-rich, and runs Ubuntu great; download it from the [website](https://www.virtualbox.org/wiki/Downloads). The Ubuntu Community is great when it comes to sharing information and there are already many tutorials on how to get an Ubuntu VM working. Although a few years old now, the answer on [AskUbuntu](http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox) is still valid today and is worth reading after you have installed VirtualBox. I highly recommend you also install the [Guest Additions](https://www.virtualbox.org/wiki/Downloads) iso to enable functionality such as drag and drop between host and guest, and window resizing.

<img align=“center” src="/media/ubuntu-vm-mac.png">

There are a few extra packages you will need out-of-the-box for snapd development so once logged in to your shiny new Ubuntu install you will need to check for, and install, updates:

<pre>
  sudo apt-get update
  sudo apt-get upgrade
</pre>

In addition to the updates you will need to install <code>git</code>, <code>bzr</code>, <code>golang</code>, and it is useful to install <code>snapcraft</code> and <code>snapcraft-examples</code> for snapping applications later:

<pre>
  sudo apt-get install git bzr golang snapcraft snapcraft-examples
</pre>

So now you have Ubuntu on your development machine, what next?

## GitHub
As stated previously, all <code>snapd</code> development occurs in GitHub. To be able to contribute to the project you will need a GitHub account so go ahead and create one. Fortunately GitHub's documentation is easy to follow so you will need to [sign up for a new account](https://help.github.com/articles/signing-up-for-a-new-github-account/) - a free account is just fine, and follow that up by [setting up Git](https://help.github.com/articles/set-up-git/). We are going to be using ssh for cloning so [generating SSH keys](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) is also needed but if this is a little too scary you can use the [HTTPS method](https://help.github.com/articles/which-remote-url-should-i-use/#cloning-with-https-urls-recommended) instead, just be aware that instructions further down and in Zygmunt's post will need to be modified slightly but I'll point that out. For reference there is a good [Git cheatsheet]([Git Cheatsheet](https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf) available from GitHub that is worth looking at.

Now we have a working Ubuntu install, Git and GitHub all set up, it is time to get developing.

## snapd development
Fortunately Zygmunt has this bit covered. He has a [great tutorial](http://www.zygoon.pl/2016/06/making-your-first-contribution-to-snapd.html) on how to fork the <code>snapd</code> project in GitHub (just go to the project and click the Fork button in the top-right corner) and set up the GO environment variables ready for development. I highly recommend using the same directory structure as Zygmunt (mine is <code>~/development/src/github.com/snapcore/snapd</code> for <code>snapd</code>) as this allows you to use his very useful <code>devtools</code> branch for useful helper functions and make sure you run the <code>get-deps.sh</code> script in the <code>snapd</code> directory to ensure you have everything set up correctly. Make sure to also get the <code>devtools</code> branch with a </code>git clone</code> and have this ready somewhere in your development directory outside of the snapd directory.

<pre>
  git clone git@github.com:zyga/devtools
</pre>

<img align=“center” src="/media/snapd-refresh-bits.png">

Development workflow is particularly nice. You hack on the code, run the tests, refresh the <code>snapd</code> code with your changes, and test them manually. The <code>refresh-bits</code> script from <code>devtools</code> starts up a separate instance of <code>snapd</code> with your changes and allows you to install snaps and test your code without affecting the host system. On my system this looks something like this (expanded a little for clarity):

<pre>
cd ~/development/src/github.com/snapcore/snapd
** hack, hack, hack **
./run-checks
** iterate until the tests are happy **
cd ~/development/src/github.com/devtools
./refresh-bits snap snapd setup run-snapd restore
** open second terminal and test changes **
</pre>

## Whats next?
Well that bit is easy, talk to the developers on [irc](https://webchat.freenode.net/?channels=snappy), sign up to the [mailing list](https://lists.ubuntu.com/mailman/listinfo/snapcraft), go find a [bug to fix](https://bugs.launchpad.net/snappy), but most importantly, get involved!
