# OpenVPN Client Gateway
#### Turning an OrangePi R1 to an OpenVPN Client Gateway
---

1. Configure an OpenVPN server
    * Use the steps on https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04 or for a lower distro version URL to generate and get your ```client1.ovpn``` file to use it in OPi R1 board 

1. Configure an OrangePi R1 as an OpenVPN Client Gateway
    1. SD Image process
        1. Download Armbian Ubuntu Server image from https://www.armbian.com/orange-pi-r1/
        1. Burn the the downloaded image file to a proper SD card by using Etcher (https://www.balena.io/etcher/)
    1. After login to Orange Pi R1, you should do the steps below:
        1. ```enxc0742bfffc6e``` similar named interface should get dynamic IP from DHCP
        1. Static ip settings:
            * ```nmtui``` is so easy-to-use network utility. You can use it to set ```eth0``` interface IP to ```34.34.34.1```
            * You can also use the file ```etc/NetworkManager/system-connections/ETH0``` in git branch as an example config file.
        1. Starting OpenVPN client:
            * Install openvpn client: ```sudo apt install openvpn```
            * Run openvpn like this: ```openvpn --config /root/client1.ovpn --daemon```            
        1. Routing settings:
            * Thx to https://unix.stackexchange.com/questions/283801/iptables-forward-traffic-to-vpn-tunnel-if-open
            * Find the proper setting file ```root/iptables-tun0.sh``` in git branch 
    1. Starting gateway after reboot
        * You can use an example init script in branch ```etc/rc.local```
1. Using the OpenVPN Client Gateway with any device:
    * Set your e.g. TV box or whatever's
        * IP: 34.34.34.34
        * GW: 34.34.34.1
        * DNS: 8.8.8.8

![](https://lh3.googleusercontent.com/GUCXC5DaWXitSj_HCexT8fcAhlt46WIxYWWvucm0PLgXX9fokSq1JeYIgSUvoVceEK_VyllniKLa4aH6tjb-kAUSikbUuFc9ud7prUQ_8vL0dm2JP8wbFO9MG6WkaqzFjiaTJHF7vIA=w430-h641-no)
