This is a version of Apple's USBProberV2 which has been fixed so as to build under 
Xcode 6.4 and OS X Yosemite 10.10.5 and deployment on 10.9, 10.10, or 10.11.
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
