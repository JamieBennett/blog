+++
Categories = ["IoT", "Security", "Ubuntu"]
Description = "Categories"
Tags = ["IoT","Ubuntu Core", "Security", "Ubuntu", "Snaps"]
date = "2017-05-10T09:29:04+01:00"
menu = "main"
title = "Why software updates matter, especially in the world of IoT"
image = "/media/snappy.png"

+++
<div align="center"><img src="/media/snappy.png"><br /></div>
## Why update?

We all know what software updates are, we see them all the time on our phones, tablets, desktops and servers. They appear as pop-ups, in the message of the day (motd), and even have dedicated applications extolling their necessity, and all for good reason. Having out of date software often means, at best a degraded user experience, at worst a security hole exploitable by hackers. When you consider that analysts such as [Gartner][0f634501] predict that the IoT will connect over 20 billion devices by 2020 the necessity for a clean and crisp update mechanism becomes paramount to any device. Exploitable devices [hit][86f31c26] [the][7a38e223] [headlines][131b923a] [often][3e3c0611] and most of the time this is due to a weakness that was not plugged fast enough or even not at all. Having connected devices means that with the right update mechanism, attacks like these should be mitigated through a fast and ubiquitous response. Of course updates are only one such security measure device makers have to take but it is one that can potentially prove to be the most future-proof.


The IoT implies a highly-connected network of "Things" which opens up the possibility to push security patches, fix bugs, and deploy new features remotely. Devices with static software do not have this ability and are stuck with whatever software the manufacturer thought was secure at the time. It's easy to see which is the correct approach but getting software updates right can be a challenge. Updates should be secure, robust, atomic with rollback support, they should be seamless to the user and automatic. This is why every [Ubuntu Core][9ed82278] system bakes update functionality in from the start.

## How Ubuntu Core keeps you safe
All software in an Ubuntu Core system is delivered as a [snap][snap_format], a self-contained, digitally-signed squashfs file carrying content and metadata mounted read-only on installation. This format is used throughout the system, including Ubuntu Core itself, and enables atomic refreshes of software across the whole stack. A small daemon runs that communicates with a 'software store', checking regularly for updates, automatically. If an update is found the daemon will download it, try to apply it, and if anything fails 'rollback' to the previous known-good version. In this way you never have a bricked device or broken software. On the store side software is updated to fix issues, security holes, and provide functionality by developers who don't have to worry about the software deployment story or if their users have downloaded the latest essential release, this is all taken care of, effectively decoupling software development from software deployment.

Lets think about this for a second. A developer who finds a security issue in their software can push a fix and have every connected device out there get that fix *automatically*. No old insecure versions, no out-of-date software. Software delivery is secure, robust, atomic, and seamless, just like it should be.
<img src="/media/software-deployment-uc.png"><br />

## Updates are systematic, not an afterthought
Several components need to work together for a complelling solution. There is more to a robust update mechanism than just a software store, or an agent, or some other over-the-air (OTA) system that is bolted on as an afterthough, every piece needs to work in synergy. The store should manage all deployable software and understand what devices need when they ask for updates. It should be able to handle delta downloads to conserve device bandwidth but also cater for delta uploads, reducing bandwidth for the developer too when they push new software to the store. It should be secure and transactional. Similarly, anything device-side should handle software rollbacks, system healthchecks, and security, be able to communicate with multiple stores and be underpinned by an authorisation mechanism that provides trust throughout the system. Using Ubuntu Core gives you all this and more.

If you are a device maker, software developer or just interested in the future of IoT software and devices I would encourage you to check out [Ubuntu Core][9ed82278] and [Snapcraft.io][Snapcraft.io] for further information.

  [0f634501]: http://www.gartner.com/newsroom/id/3598917 "Gartner connected things prediction"
  [131b923a]: http://www.techradar.com/news/dangerous-backdoor-exploit-found-on-popular-iot-devices "DblTek exploit"
  [3e3c0611]: http://www.hometoys.com/article/2017/03/cia-exploits-of-iot-devices-what-lessons-can-we-learn-/36301 "CIA backdoors"
  [86f31c26]: https://thenextweb.com/gadgets/2017/01/31/netgear-vulnerability-router-bypass/#.tnw_OmpwXH06 "Netgear exploit"
  [7a38e223]: https://www.wired.com/2017/03/security-news-week-iot-teddy-bear-leaked-millions-parent-child-voice-recordings/ "Teddy bear exploit"
  [9ed82278]: https://www.ubuntu.com/core "Ubuntu Core"
  [snap_format]:  https://github.com/snapcore/snapd/wiki/Snap-format "Snap Format"
  [Snapcraft.io]: http://www.snapcraft.io "Snapcraft.io"
