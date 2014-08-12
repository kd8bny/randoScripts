This is a collection of scripts that I have built and maintained using a variety of different sources for Linux. All of my scripts have been built and tested using the Ubuntu distribution.

# fstrim
This bash script enables Linux to auto-remove pages of data within an SSD. This is required because the smallest write to a SSD is a page and the smallest delete is a page: (page << block).

## Info

[Read for very useful information](http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/)
- Location: "/etc/cron.weekly/"
- Logs are located in "/var/log/fstrim.log"

**LVM Partition Important!**
We have to make sure *issue_discards* is enabled.

Run $ cat /etc/lvm/lvm.conf | grep issue_discards

The value should be = 1