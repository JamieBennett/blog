+++
Categories = ["Development", "Linux", "Snappy"]
Description = "Cross distro packaging with Snaps"
Tags = ["Development", "Linux", "Snappy", "Snaps"]
date = "2016-06-16T18:41:40+01:00"
menu = "main"
title = "Are snaps really cross distro?"

+++
Yesterday we announced the new home for everything snaps and Snapcraft, [snapcraft.io](http://www.snapcraft.io), and at the same time made available the cross-distribution work that really does means snaps can run on virtually any Linux distribution. Today we have enabled support for Debian, Arch, Gentoo, Fedora, and of course Ubuntu and all its flavours but enabling more including OpenSUSE, CentOS, Elementary, Mint, OpenWrt and others is in the works. 

The announcements was met with a mostly positive response which, given that Linux packaging has been an issue for so many people and for so long, is hardly surprising. This particular problem has resulted in the community creating a few different initiatives such as AppImage and OrbitalApps, tackling the problem in different ways and all of which have their own merits and limitations. In my opinion (of course slightly biased but based on technical fact), snaps are the best solution for a complete cross-platform universal package format whether that be for the Linux desktop, IoT and mobile devices, or the server. Snaps are surprisingly easy to use, encompass industry-leading security with AppArmor, Seccomp filters, and more, and all with the very familiar and popular Ubuntu development workflow. A special mention has to go to the tooling as well; Snapcraft is already pretty awesome but week after week new features are being added to improve this further and snapd, the tool that runs snaps in a confined environment, is seeing so much innovative, open development that these two are great examples of projects to get your teeth into if you are a developer, tester, or just want to dabble in an open source project.

There has been some doubt that snaps really could run on multiple distributions and, as part of the team who tested this extensively, I can definitely confirm this is the case. I played around with several native installations and VMs over the course of last week and the results were super positive. As the saying goes, a picture is worth a thousand words so I took a couple of screenshots. Enjoy!

<img align=“center” src="/media/snapd-cross-distro.png">
