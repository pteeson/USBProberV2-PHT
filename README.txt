2019-03-16 This is a version of Apple's USBProberV2 which has been fixed
so as to build under Sierra macOS 10.12.6 Using Xcode 8.3.3 with 10.12 SDK.

Also compiles on Sierra using Xcode 9.2 for High Sierra macOS 10.13
but not tested in High Sierra as I have not installed it.

Summary of changes made:
1. In file BusProberSharedFunction.m replaced all occurences of _verify_noerr with
new macro __Verify_noErr. Old macros no loger supported in Sierra.
See AssertMacros.h

2. Sierra requires macOS 10.11 as minimum SDK. For Xcode 8.3.3 changed Build settings
Base SDK to Latest macOS (macOS 10.12) and Deployment Target macOS 10.12.

I have not bothere to try building for El Capitan as I never installed it.
But it wil probbably work because when I set the Deployment Target to macOS 10.11.
it compiled fine. The only Warning was about linking with certain /usr files
from macOS 10.12 while compiling with macOS 10.11.
(I don't think it's going to be fragile but you have been warned)

3. Comment out duplicates in file BusProberDevice.h

4. Fixed many Warnings of type Value Conversion issue in many files.

5. Fixed several deprecations -7 still left over from Previous upload

6. Fixed KextInfoGatherer.h and restored KextInfoGatherer to original soure.
Removed files OSKext.h OSKextLib.h, OSKextLibPrivate.h, OSReturn.h

====================== Previous upload ==========================

This is a version of Apple's USBProberV2 which has been fixed so as to build under
Xcode 6.4 and OS X Yosemite 10.10.5 and deployment on 10.9, 10.10,
NOTE: 2019 this needs Sierra I think for 10.11.

No other OS X deployment versions have been tested.
For OS C versions prior to 10.9 use Apple's distribution.

I may at some point try it on 10.11 El Capitain when I use it myself. But don't count on that.

Any Modifications or Additions made by me are identifed by the comment string // PHT,
and are licensed to you under the same terms as the APPLE PUBLIC SOURCE LICENSE which can be
found at <http://www.opensource.apple.com/apsl/>.

The file 'USBProberV2 - PHT log of fixes.txt' describes the details of the steps taken to upgrade
from Apple's original OS X 10.8.5 Mavericks open source code in the IOUSBFamily.

======= DONE Step   I - try to build got 3 Errors - eliminated them.
======= DONE Step  II - clear 31 warnings- 1 Validate 5 Klog and 25 USBPprober
                        7 Deprecations still to remove -see below TO DO
======= DONE Step III - Restore the function of the Kernel Extensions tab

=======	TODO Step IV - What's left to do
7 Warnings 'AuthorizationExecuteWithPrivileges' is deprecated: first deprecated in OS X 10.7
The plan is to re-write and add code to do it the recommended way with an embedded Helper app.
However since these are only related to loading the logging kext need to research before proceeding.

(a) just what the kext actually does if loaded
(b) is that still supported in El Capitain and the next version of OS X (Safari?)
(c) what alternatives, preferably from userland without hte need for a kext.
