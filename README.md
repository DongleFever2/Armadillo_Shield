# Armadillo_Shield

2015 Project Awesome

First edit - silenttrace

Second edit -

What has been done so far….

One must build the operating system. This has been done three or four times now and someone else hopefully wrote the notes.
Task: Someone must research the easiest method to partition the hard drive through the GUI install. You want 75% of the disk space to go to the /var directory.
It is okay and preferred if this step requires a pencil, paper, and calculator. The notes should explain what to expect and how to do the steps, but they will need to do some simple math - because we can’t predict the hard drive size of the individual home users gateway system.
Need to comment out the cdrom boot option from /etc/apt/source.list file.
You also need to add:
deb http://download.webmin.com/download/repository sage contrib
deb http://http.us.debian.org/debian stable main contrib non-free
http://security.debian.org stable/updates main contrib non-free
Then run (which will force the OS to re-source the distribution sources and update the system)
apt-get update
apt-get upgrade
apt-get install ntop
it will appear to fail, let it and then enter
apt-get install —fix-missing
apt-get install munin
apt-get install webmin
apt-get install shorewall6
apt-get autoremove
apt-get clean
apt-get auto clean
To get ntop to run, enter:
ntop -A
/etc/init.d/ntop start
may be a pain so I tried top -i eth0. The problem is this dumps to the screen and so you lose the terminal. This must be fixed so it runs in the background. To see webpage of this data
http://127.0.0.1:3000; or
http://10.0.91.141:3000
To get webmin up and running:
change line allow=127.0.0.1 to allow=10.0.91.141 (or whatever client you want to have access to this server, so something from within your local lan.)
enter /etc/init.d/webmin restart (need to make sure this happens at reboot)
change startup=0 to startup=1 in /etc/default/shorewall/shorewall.conf
open browser https://10.0.91.141:10000

We need people to focus on webmin and shorewall6 to make sure its up and running correctly. In other words proper setup of whitelisting and blacklisting, denial of all inbound traffic to the external interface except to ssh server and vpn server. All outbound traffic from the external interface that originated internally to the gateway is okay. Only allow inbound ssh to the internal interface of gateway while the remaining internal traffice to the internal interface is passed out to the web through the external interface.

Ask questions…