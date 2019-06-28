+++
Categories = ["Development", "Ubuntu"]
Description = "How-to showing how to run Ubuntu Snappy Core on Mac OSX using VirtualBox"
Tags = ["Development", "Ubuntu"]
date = "2015-11-09T14:09:32Z"
menu = "main"
title = "Running Ubuntu Snappy Core Virtualised on Mac OSX"

+++

Although most of the documentation out there today shows you how to run Ubuntu Snappy Core on an Ubuntu desktop, it is also pretty simple to do this on Mac OSX. In short:

Download the Ubuntu Snappy Core image from:

    http://releases.ubuntu.com/15.04/

You will need the amd64 version of Snappy.

Unarchive the file:

    unxz ubuntu-15.04-snappy-amd64-generic.img.xz 

Then convert the image into something that VirtualBox can run:

    qemu-img convert -f raw -O vmdk ubuntu-15.04-snappy-amd64-generic.img ubuntu-15.04-snappy-amd64-rpi2.vmdk

At this point you want to create a new VM with VirtualBox. Make sure you create a Linux Ubuntu image but when you get to the Hard drive section select "Use an existing virtual hard drive file". Navigate to your .vmdk image and click create. Now, when you start the VM you should be greated (pretty quickly) with the login prompt from Snappy.

<div align="center">
<img src="/media/virtualbox.jpg" title="VirtualBox">
</div>
