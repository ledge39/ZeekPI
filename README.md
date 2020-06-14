# ZeekPi
Zeek IDS on Raspberry Pi 4

## Update OS

`sudo apt update && sudo apt upgrade`

#### Dependencies that need to be installed:

`sudo apt-get install bison cmake flex g++ gdb make libmagic-dev libpcap-dev libgeoip-dev libssl-dev python-dev zlib1g-dev swig`

## Download and Install 

`wget https://download.zeek.org/zeek-3.0.6.tar.gz`

`tar xvzf zeek-3.0.6.tar.gz`

`cd zeek-3.0.6/`

`./configure`

`make && sudo make install`

> [!TIP]
> Warning this step will take 2+ hours

## Configure Network

`sudo nano /etc/dhcpcd.conf`

> `denyinterfaces eth0`

`sudo nano /etc/network/interfaces.d/zeek`

> `auto eth0`
> 
> `  iface eth0 inet manual`
> 
> `  up ifconfig 0.0.0.0 up`
> 
> `  up ip link set eth0 promisc on`
> 
> `  down ip link set eth0 promisc off`
> 
> `  down ip link set eth0 down`

`sudo setcap cap_net_raw,cap_net_admin=eip /usr/local/zeek/bin/zeek`

`sudo setcap cap_net_raw,cap_net_admin=eip /usr/local/zeek/bin/zeekctl`

## Configure Zeek

`export PATH=/usr/local/zeek/bin:$PATH`

`sudo nano /usr/local/bro/etc/networks.cfg`

> `192.168.1.0/24 Private IP space`

> [!NOTE]
> You may also need to configure node.cfg and broctl.cfg

`sudo chown pi -R /usr/local/zeek`

`sudo chgrp pi -R /usr/local/zeek`

`zeekctl`

`[ZeekControl] > install`

`[ZeekControl] > cron ?`

`[ZeekControl] > status`

`[ZeekControl] > start`

## Install EasyBeats

`sudo apt install git`

`git clone https://github.com/josh-thurston/easyBEATS.git`

`cd easyBEATS`

`sudo nano easyBEATS`

`sudo chmod 755 easyBEATS`

`./easyBEATS`

`sudo nano /etc/filebeats/filebeat.yml`