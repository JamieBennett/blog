+++
Categories = ["Development", "Security"]
Description = "An introductionto Trustzone for Android Mobile Security"
Tags = ["Development", "Security", "Android"]
date = "2015-02-22T17:13:52Z"
menu = "post"
series = "Android Security"
title = "TrustZone For Android Mobile Security"

+++
Recently I was asked to provide a quick, high-level introduction to TrustZone and how it could potentially improve the security on Android platforms. Any response to this is tricky: TrustZone is just a mechanism built in to a platform that if unused can do very little for device security but when utilised to its fullest, can create a totally seperate environment dedicated to protecting your most important secrets. But first a bit of background.

According to Bloomberg [^1] ARM's chip designs are found in 99% of the world's smartphones and tablets; 2013 alone saw ARM's partners ship over 10 billion chips (source: ARM Strategic Report 2013). Popular devices such as the Apple iPhone and iPad, Amazon's Kindle, and Samsung's flagship Galaxy series all use a Central Processing Unit (CPU) based on an ARM design. In 2004 ARM released its design for a hardware-enforced parallel execution environment for the PB1176 and ARMv7 architectures that was adopted into all later application processor designs.

TrustZone itself is an implementation of device-level security utilizing extensions to the CPU and Advanced Microcontroller Bus Architecture (AMBA), or memory bus. By connecting all these components together in a homogeneous architecture it is possible to contruct two distinct 'worlds', a "*Secure World*" and a "*Non-Secure World*" (or "*Normal World*") [^2]. The two modes are orthogonal to each other with the Secure World enjoying full access to all memory regions and priviledged CPU areas whereas the Normal World can be restricted. This arrangement is configured during the boot process. The interface between the two worlds is governed by a special Secure Monitor Mode, accessible via an interrupt instigated with the Secure Monitor Call (SMC) instruction. Identification of which world the processor is currently executing it is possible by the use of a extra 'flag' known as the NS, or Non-Secure bit. All components that wish to use the functionality provided by TrustZone must beaware of this flag.

With TrustZone it is possible to isolate an area of the CPU, memory, and peripherals for use by a trusted software component called a Trusted Execution (TEE) [^2] or other such privileged software. For example, Android's implementation of the core crytographical keystore functionality, [KeyChain]
(http://developer.android.com/reference/android/security/KeyChain.html), can use hardware components such as TrustZone, Sim Card, or Trusted Platform Module (TPM), to enhance overall security. By using TrustZone a device can provice secure software functionalty, backed up by the hardware it is running on.

It is clear that with more widespread use TrustZone could benefit an increasingly mobile society who expect to do the most secure of operations with their devices. 

[^1]: http://www.bloomberg.com/bw/articles/2014-02-04/arm-chips-are-the-most-used-consumer-product-dot-where-s-the-money]
[^2]: J. Winter. Trusted computing building blocks for embedded linux-based arm trust- zone platforms. In Proceedings of the 3rd ACM workshop on Scalable trusted com- puting, pages 21–30. ACM, 2008.
[^3]: T. Alves and D. Felton. Trustzone: Integrated hardware and software security. ARM white paper, 3(4):18–24, 2004.