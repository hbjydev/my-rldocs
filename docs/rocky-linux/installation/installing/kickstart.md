# Kickstart Installation

Rocky Linux 8 also supports a different form of installation, using a standard
configuration file called a
[Kickstart](https://en.wikipedia.org/wiki/Kickstart_(Linux)).

It allows you to statically define all required configuration in order to
perform what's known as an _unattended install_.

!!! Note
    For the purposes of this document, we assume you have some amount of Linux
    administration knowledge and are familiar with the basic steps required to
    _graphically_ install Rocky Linux 8, as Kickstart files take away a lot of
    the abstraction of a GUI.


## What is a Kickstart?

Kickstarts, originally developed by Red Hat for RHEL, but employed by most
distributions utilizing Anaconda as an installation system (like Fedora), are
a way to pre-configure the installation tasks the install media should carry
out before even running the installer.

They allow you to (either fully or partially) automate the Rocky Linux install
process.

They allow you to script most, if not all, installation tasks within Anaconda,
exposing some options that aren't even configurable graphically. Through a
Kickstart, you can configure things like NTP servers, DNS settings, user
accounts, firewall settings, how drives should be partitioned, and more.

Kickstarts become increasingly useful at larger scale, where you need to roll
out the same configuration of a host to many hosts at once.

Kickstart _files_ can be kept on a single, shared server, and can be served to
other hosts by network protocols like HTTP and FTP by adding a boot argument to
the GRUB entry before booting into the installer.

All kickstart files and their output logs are stored in `/tmp` on the installed
system to assist in debugging a faulty or failed installation.
