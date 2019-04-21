# OpenVPN Client Gateway
#### Turning an OrangePi R1 to an OpenVPN Client Gateway
---

1. Configure an OpenVPN server
    * Use the steps on https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04 or for a lower distro version URL to generate and get your ```client1.ovpn``` file to use it in OPi R1 board 

1. Configure an OrangePi R1 as an OpenVPN Client Gateway
    1. SD Image process
        1. Download Armbian Ubuntu Server image from https://www.armbian.com/orange-pi-r1/
        * Burn the thw downloaded image file to a proper SD card by using Etcher (https://www.balena.io/etcher/)
    * After login on Opi, you should do the steps below:
        1. Starting OpenVPN client:
            * Install openvpn client: ```sudo apt install openvpn```
            * Run openvpn like this: ```openvpn --config /root/client1.ovpn --daemon```
        * Static ip settings:
            * ```nmtui``` is so easy-to-use network utility. You can use it to set eth0 IP to ```34.34.34.1```
            * You can also use the file ```etc/NetworkManager/system-connections/ETH0`` in git branch as an example config file.
        * iptables setting
            * Thx to https://unix.stackexchange.com/questions/283801/iptables-forward-traffic-to-vpn-tunnel-if-open
            * Find the proper setting file ```root/iptables-tun0.sh``` in git branch 
    * Starting gateway after reboot
        * You can use an examle init script in branch ```etc/rc.local```
* Using OpenVPN Client Gateway with any device:
    1. Set your e.g. TV box or whatever's
        * IP: 34.34.34.34
        * GW: 34.34.34.1
        * DNS: 8.8.8.8

![image]()
