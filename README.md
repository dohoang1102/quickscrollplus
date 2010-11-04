QuickScrollPlus - an extension of QuickScroll2 by KennyTM~, by Nathan Broadbent (www.f-77.com)
==============================================================================================

= NOTE: This is under development, but has not been started yet. I just decided to write the README first :)

This is a fork of QuickScroll2, including bug fixes and 'tilt' scrolling. Will be tested and working iOS 4.1, lower versions are unsupported until they can be tested by someone else.
See here for the original project wiki: http://code.google.com/p/networkpx/wiki/Using_QuickScroll

Please note: This application will only work on a jailbroken iPhone.


= Application Usage

To use the tilt scrolling feature: 

1) Position your iPhone at a comfortable reading angle, and then tilt it a few degrees away from you. This will be the zero calibration point.
2) Activate the scrollbars with your prefered method.
3) Double tap either the horizontal or vertical scroll bars. They will turn green to indicate that tilt scrolling is now enabled.
4) Tilt your iPhone back towards you, and the page will start to scroll. You can control or reverse the speed by adjusting the tilt angle.
5) To turn off the tilt scroll feature, double tap the scroll bars again.


= Compiling and installing from source

=== In order to compile and install this application, you must have the following files on your Mac:

* iOS 4.1 SDK or higher (including iPhone 3.2 SDK)
** Sign up for a free apple developer account to download.
* networkpx repository (the original QuickScroll2 source code, and other required files) - check it out in a neighboring directory
** $ svn checkout http://networkpx.googlecode.com/svn/trunk/ networkpx-read-only
* iPhone Private Frameworks repository - also check these out in a neighboring directory
** $ git clone git://github.com/kennytm/iphone-private-frameworks.git
** # You must then copy IOSurfaceAPI.h from your system into ./include/IOSurface (we can't distribute this file, as per the Apple license)
** $ cd iphone-private-frameworks && cp /System/Library/Frameworks/IOSurface.framework/Headers/IOSurfaceAPI.h include/IOSurface/
* ldid in /usr/local/bin/
** It was a bit tricky to find, so I've included it in the repository. Run the following from the repo directory:
*** $ sudo cp ldid /usr/local/bin/ && sudo chmod 755 /usr/local/bin/ldid

- See here for the original wiki that these requirements are based on: http://code.google.com/p/networkpx/wiki/Compiling_networkpx

=== Modify the paths in ./src/Makefile if necessary.

iPhonePrivateFrameworksPath=../../iphone-private-frameworks
networkpxPath=../../networkpx-read-only 

=== Compile and package

$ ./makedeb.sh

=== SSH and install on iPhone

$ scp hk.ndb.quickscrollplus-0.3-1a.deb root@{{iPhone IP}}:/tmp
$ ssh root@{{iPhone IP}}
$ cd /tmp && dpkg -i hk.ndb.quickscrollplus-0.3-1a.deb

- Reboot your iPhone, and your done!