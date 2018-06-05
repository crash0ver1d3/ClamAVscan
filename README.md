# ClamAVscanSetup
Tool utilizing ClamAV, to perform AV scan on USB drive once mounted to raspberry Pi (or RHEL device)
Document for setting up raspberry Pi USB scanner:
The follow are pre-requisites for the scan script to run properly.
Raspbian OS

$apt-get update 
$apt-get install clamav
$apt-get install usbmount
$apt-get install xscreensaver

su -
~~ This section creates a a directory in /var/log to save the results of anti-virus scan on USB
~~ The directory name can be changed out to be whatever you choose, but you must update that name in the script that runs
~~ the auto scan on the USB drive  (/etc/usbmount/mount.d/01_usb_autoscan)
# cd /var/log
#mkdir clamscanz
#chmod 755 clamscanz/
#pwd
#/var/log
#cd /etc/usbmount/mount.d
#vi 01_usb_autoscan    

script contents
~~ While using the /dev/pts/0 output, this will send the screen output to the first logcial SSh connection
~~ While using the /tty/0 ouptut, this will put the console connection of the raspberry pi.


Configuring Screen Saver to not appear in Xwindow mode
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Stop text terminals from blanking
From GUI, go to Screensave, and set to none. This will keep the pi screen from blanking out

I had no luck with these, but left the config set this way anyways.
change in /etc/kbd/config these two:
BLANK_TIME=0
POWERDOWN_TIME=0

Stop Xsession from blanking
Additional info https://wiki.archlinux.org/index.php/Di ... _Signaling
Add these lines to /etc/xdg/lxsession/LXDE/autostart
@xset s noblank 
@xset s off 
@xset -dpms

