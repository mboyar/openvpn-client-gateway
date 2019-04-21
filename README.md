# OpenVPN Client Gateway
#### Turning an OrangePi R1 to a OpenVPN Client Gateway
---

1. Configure an OpenVPN server
    1. Use the steps on https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04 or for a lower distro version URL
    * Generate and get your ```client1.ovpn``` file to use it in OPi R1 board.
* SD Image process
    1. Download Armbian Ubuntu Server image from https://www.armbian.com/orange-pi-r1/
    * Burn the thw downloaded image file to a proper SD card by using Etcher (https://www.balena.io/etcher/)
* After login process 
    1. openvpn client line
    * static ip setttings
    * iptables lines
    * rc.local lines
* Using
    1. set your TV box or whatever's
        * IP: 34.34.34.34
        * GW: 34.34.34.1
        * DNS: 8.8.8.8
