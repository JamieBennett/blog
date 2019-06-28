+++
Categories = ["Snaps", "Raspbian"]
Description = "Using Snaps on Raspbian"
Tags = ["raspbian", "snaps"]
date = "2018-04-13T15:47:22+01:00"
menu = "main"
title = "Using Snaps on Raspbian"
image = "/media/rpis.jpg"

+++

<div align="center"><img src="/media/rpis.jpg" /></div>

Who isn't a fan of the [Raspberry Pi](https://www.raspberrypi.org/)? The little, cost-effective single-board computer that has so many uses, in fact at home I have 4 doing various things from monitoring temperature and humidity in my greenhouse to serving up a dashboard interface for my home automation solution, both projects which I will write more about in future posts. But what makes the Raspberry Pi even better, well [Snaps](https://snapcraft.io/store) of course. I run Ubuntu on my devices which comes baked in with Snap support but the excellent Raspbian is also a popular choice of OS. As Rasbian is based on Debian it too can run Snaps with a few simple commands.

    sudo sed -i 's/main/main contrib non-free/' /etc/apt/sources.list.d/raspi.list

    # Not required but silences ERROR regarding the memset, memcpy preloaded libs for the Pi
    sudo sed -i 's/\usr/#\/usr/` /etc/ld.so.preload

    sudo apt update
    sudo apt install snapd
    sudo reboot

After a reboot typing ``snap install hello-world`` should work (or any other snap name, use ``snap find`` to see more software).

Thanks to [Martin Wimpress](https://flexion.org/) for the above commands.
