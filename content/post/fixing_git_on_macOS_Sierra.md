+++
Categories = ["Development", "MacOS"]
Description = "A quick tip showing you how to fix git after upgrading to MacOS X Sierra"
Tags = ["Development", "MacOS", "Git", "Tip"]
date = "2016-09-13T12:55:14+01:00"
menu = "main"
title = "Fixing Git on MacOS X Sierra"

+++

If, like me you have upgraded to the Mac OS X Sierra beta you may find that Git is broken from the command line. The error I was seeing was:

<pre>
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
</pre>

It turns out that the developer tools are borked on upgrade so need reinstalling. To do that you need to run:

<pre>
xcode-select --install
</pre>

After a short download and installation everything should be back to normal.
