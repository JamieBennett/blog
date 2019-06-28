+++
Categories = ["Linux", "Ubuntu", "Paper-Free"]
Description = "Categories"
Tags = ["Linux", "Ubuntu", "Paper-Free"]
date = "2015-12-30T21:35:27Z"
menu = "main"
title = "Fujitsu SnapScan 1300i with Ubuntu"

+++

I've been using the [Fujitsu ScanSnap 1300i](http://www.fujitsu.com/uk/products/computing/peripheral/scanners/scansnap/s1300i/) on Mac OS X for some time now in the pursuit of a paperless life but now that I am using Ubuntu more and more it was apparent that I was going to have to get this little scanner working on Linux. Searching the internet threw up a few interesting articles but nothing worked 100%. In the end the steps I used under Ubuntu 15.10 were:

Install ***sane*** and ***gscan2pdf***:

    $ sudo apt-get install sane gscan2pdf

Download the scanner firmware from http://www.openfusion.net/public/files/1300i_0D12.nal copy it to the relevant directory:

    $ wget http://www.openfusion.net/public/files/1300i_0D12.nal && sudo mkdir /usr/share/sane/epjitsu && sudo cp 1300i_0D12.nal /usr/share/sane/epjitsu

Open up the scanner lid first then initialise it with:

    $ sudo scanimage -L

Run the gscan2pdf application:

    $ gscan2pdf

You can tweak some of the scanner options by clicking the scan button and playing around with the pop-up box tabs. For me the most important were to select duplex as I regularly scan double-sided documents and to select colour.

Happy scanning.

