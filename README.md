This is a collection of scripts that I have built and maintained using a variety of different sources for Linux. All of my scripts have been built and tested using the Ubuntu distribution. 

If you have any questions please contact me: ***kd8bny@gmail.com***

# [Writeup ](http://kd8bny.blogspot.com/2014/08/useful-linux-scripts.html)

# Backlight
In default operation Ubuntu sets the backlight of your laptop to maximum brightness on every boot. Although this is an extreme issue of any sort it can be avoided with the raw power of Linux. All that is required for this fix is to edit **/etc/rc.local**

### Info

[Writeup](http://kd8bny.blogspot.com/2014/08/another-useful-script-better-brightness.html)

*IMPORTANT:* If you have already edited your *rc.local* do **NOT** replace it with my copy. (You know if you did this) ;)
- Location: "/etc/rc.local"
- If the location *"/sys/class/backlight/acpi_video0/brightness"* is ineffective use 
	*"/sys/class/backlight/intel_backlight/brightness"*

#### Install
1. Find a value you want by adjusting brightness in the system
2. $cat /sys/class/backlight/acpi_video0/brightness
3. Open *rc.local* and replace value "*VALUE_HERE*"
4. $sudo mv rc.local /etc
5. $sudo chmod +x /etc/rc.local

# fstrim
This bash script enables Linux to auto-remove pages of data within an SSD. This is required because the smallest write to a SSD is a page and the smallest delete is a page: (page << block).

### Info

[Read for very useful information ](http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/)
- Location: "/etc/cron.weekly/"
- Logs are located in "/var/log/fstrim.log"

**LVM Partition Important!**
We have to make sure *issue_discards* is enabled.

Run $ cat /etc/lvm/lvm.conf | grep issue_discards

The value should be = 1

# syncGrive
Due to the lack of a dedicated Linux client for Google drive, the fantastic team **The Fan Club" created a 3rd party answer known as [grive](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)

### Info
*IMPORTANT:* By default grive does NOT delete files that have been removed in drive. The application instead moves files to the **.trash/** directory. This script auto deltes these files once drive is synchronized. If you want to take care of this your self comment out: 

line 10:: **(cd $account && rm -r .trash >> $LOG)** 

The script assumes the grive main directory is under **~/grive**. if this is incorrect change line 3 to match accordingly.

### Install

$sudo apt-add-repository http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools

$sudo apt-get update && sudo apt-get install grive

# xbindkeys
This is my edited copy of xbindkeys for a Logitech MX pro mouse, but this can be edited for any keyboard of mouse combination. Please read the writeup for more information 

### Info

[Writeup ](http://kd8bny.blogspot.com/2013/12/become-key-binding-pro-using-xbindkeys.html)

- Required packages
  - xbindkeys && xautomation
- Location: "~/"

