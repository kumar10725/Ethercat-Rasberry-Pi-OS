# Ethercat-Rasberry-Pi-OS
Instructions on how to install ethercat on raspberry pi OS


#first install realtimepi OS

https://github.com/guysoft/RealtimePi

# install tools
`sudo apt install build-essential git`

#then install relevant kernal headers from
https://github.com/kdoren/linux/releases/

#Installation Instructions
```
sudo apt install -y  build-essential libtool automake tree dkms
sudo apt-get install mercurial
git clone https://github.com/icshwi/etherlabmaster
cd etherlabmaster
rm -rf etherlabmaster-code
# get latest version
git clone https://gitlab.com/etherlab.org/ethercat.git etherlabmaster-code
make init
echo "ENABLE_CYCLES = NO" > configure/CONFIG_OPTIONS.local
make build
make install
echo "ETHERCAT_MASTER0=eth0" > ethercatmaster.local
make dkms_add
make dkms_build
make dkms_install
make setup
# Reboot or start manually
sudo systemctl start ethercat
```
