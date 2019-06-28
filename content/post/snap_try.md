+++
Categories = ["Development", "Linux", "Snappy"]
Description = "Trying snaps without creating a squashfs"
Tags = ["Development", "Linux", "Snappy", "Snaps"]
date = "2016-07-01T20:32:12+01:00"
menu = "main"
title = "snap try: The quick way to package snaps"

+++

This weeks snippet is all to do with improving the snap developer experience.

Since the release of snapd 2.0.8 we have added one of the most useful tools for snap developers:

<code>snap try</code>

What this does is effectively mounts any folder containing an unpackaged snap at <code>/snap/snapname</code> as a writeable folder allowing quick iteration during the packaging process. No longer do you have to create a read-only squashfs snap and install it to try out your latest changes and this speeds up the workflow tremendously. The process I use from the package directory is:

<pre>
% snapcraft prime
% snap try prime
% /snap/bin/snapname
... test/hack ....
% snap remove <snapname>
</pre>

When you are happy with your testing you can create the real snap file with:

<pre>
% snapcraft
</pre>

Happy snapping!
