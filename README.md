# ZeekPi
Zeek IDS on Raspberry Pi 4

#### Update OS

`sudo apt update && sudo apt upgrade`

#### Dependencies that need to be installed:

`sudo apt-get install bison cmake flex g++ gdb make libmagic-dev libpcap-dev libgeoip-dev libssl-dev python-dev zlib1g-dev swig`

#### Download and Install 

`wget https://download.zeek.org/zeek-3.0.6.tar.gz`

`tar xvzf zeek-3.0.6.tar.gz`

`cd zeek-3.0.6/`

`./configure`

`make && sudo make install`

#### Configure Zeek

