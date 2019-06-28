+++
Categories = ["Development", "Running"]
Description = "Categories"
Tags = ["Development", "Security", "Android"]
date = "2015-03-15T19:56:29Z"
menu = "post"
series = "Android Security"
title = "Trusted Execution Environments in Android"

+++
Continuing on from my post about TrustZone it seems that there is a lot of interest in hardware-backed security for Android and what you can do with it. One of the most interesting things that a hardware-isolated area can do for devices, whether that be a dedicated co-processor or technology such as TrustZone, is to provide a trusted enviroment dedicated to protecting your most valuable assets and the operations that are performed on them. Installing something like a micro operating system in this divide can give you a lot of features that the main OS just cannot gain access to and is the thrust of standards bodies such as Global Platform [^1]. This micro OS, or to use the popular parlance: a Trusted Execution Environment (TEE), is becoming more important in a world of one-click / swipe / wave-a-device payments and device authorisation and over the coming years will see a surge in popularity not only from independant vendors but from the large OS vendors too. But lets take a step back.  

The concept of a Trusted Execution Environment is to provide a secure area of the main processor, memory, and peripherals, that can be used to perform privileged operations. First defined by the Open Mobile Terminal Platform (OMTP) forum in their Advanced Trusted Environment:OMTP TR1 standard [^2] and later adopted by Global Platform in their standardisation effort, the TEE has become a bridge between pure software security mechanisms and hardware-only solutions. The TEE uses the concept of isolation that technologies such as TrustZone enable to execute in the processors Secure World mode.

The TEE can be a fully-functional operating system offering software developers the opportunity to create Trusted Applications: applications that reside in the Secure World and perform security-critical functions outside of the control of the main operating system running in the Normal World. An example of such a Trusted Application can be a Trusted User Interface (TUI) - a display that is presented to the user completely protected by the Secure World and inaccessible to the main operating system such as Android. The interface could display sensitive information such as passwords and be confident that attacks such as screen scraping or video buffer capture would not reveal anything.

It is clear that the popularity of TEEs is increasing. Based on one commercial TEE vendors press releases the adoption rate of the Trustonic TEE is reported to be over 100m devices every 6 months (source: http://www.trustonic.com - figures from February 2014 to July 2014) although wide-spread utilisation by third-party developers is yet to be exploited. Ekberg et al [^3] attribute this to a lack of access to the TEE stating that ***"Despite TEE’s large-scale deployment, there’s been no widely available means for application developers to benefit from its functionality as mobile device manufacturers have restricted TEE access to their internal use cases."***, but also admit that standardisation could potentially solve this issue. Recent announcements by companies such as Linaro point to a more open access model [^4] but we are yet to see commercial devices with OP-TEE technology.

In short, TEEs are here to stay and I expect that the likes of Apple and Android will open up access to this trusted area for more developers to enhance the security of their applications in the near future.

[^1]: http://www.globalplatform.org
[^2]: http://www.gsma.com/newsroom/wp-content/uploads/2012/03/omtpadvancedtrustedenvironmentomtptr1v11.pdf
[^3]: The Untapped Potential of Trusted Execution Environments on Mobile Devices - Ekberg, J.-E. and Kostiainen, K. and Asokan, N.
[^4]: https://www.linaro.org/blog/core-dump/op-tee-open-source-security-mass-market 
