## Overview
WOL (Wake On LAN) allows the waking of a suspended or shutdown system over LAN.

Note that not every system, especially laptops, support WOL or waking from shutdown.

A static DHCP lease (also known as a static Local IP) for your host in your router is recommended to improve reliability and is required for WOL over the Internet. See: https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#static-dhcp-reservation

WOL over Wi-Fi is usually unstable. It is always recommended to have a wired connection for the host when possible.

WOL has to be enabled both in the UEFI/BIOS and OS in order to function.

## UEFI/BIOS Setup
*These steps may differ depending on your system*

First, enter the UEFI/BIOS. Pressing the __delete__ key during boot usually works, you can also try __F2__ or __F12__. Alternatively on Windows 8+ you can hold the __Shift key while Rebooting__ Then navigate to Troubleshooting>Boot to UEFI.

Look for a setting usually found in "Power" or "PCI sub system" called "Power On By PCI Device" or "Wake-on-LAN" or similar. These need to be enabled.

## Windows Setup
Open Device Manager, You can do this by right-clicking the Windows Icon. Then navigate to "Network Adapters" and Right-click your Adapter, Then go to the Advanced tab. In the list look for "Wake on Magic Packet" and enable it, it is usually towards the bottom. "Wake on Magic Packet from system shutdown" allows for Waking from shutdown. __Wake on pattern should remain Disabled!__ Having it Enabled can result in random system wakes from normal network scans and such.

If you do not see the options listed above then the NIC (Network Interface Card) does not support WOL.

Also in adapter properties under the "Power Management" tab enable "Allow this device to wake the computer" and its sub option.

## Linux Setup
In the Terminal run `ifconfig -a` and note the desired eth#.

Install "ethtool" if not already installed, run `sudo ethtool eth#` and replace eth# with noted. Check the output, if there is a "G" next to "Supports Wake-on" then the NIC supports WOL. Run `sudo ethtool -s eth# wol g` again replace eth# with noted.

## Internet WOL
DDNS or a static Public IP is a requirement. see https://www.noip.com/ a DDNS service.

WOL is not designed to work over WAN (Wide Area Network, AKA Internet), but it can be done in a few ways, some safer than others. The list below is the order of recommended methods. Most methods require some other device that is always online and connected you your __Hosts__ local network.

- Host a VPN server. You will need some other device that is always online and connected to the Hosts network to act as a VPN server. You will also have to have the ability to port forward on your router. The WOL packet can be sent from the Moonlight client to the sleeping host via VPN. Such devices include but are not limited to;
    - Routers, many can run a VPN server.
    - A RPI (Raspberry PI) or other similar SBC.
    - A NAS. (Network Attached Storage) Basically a Server, a NAS can host a variety of servers including VPN servers. Many customer NAS devices have a baked-in VPN utility.
- Have another device wake the system. You will need some other device that is always online and connected to the Hosts network to act as in essence a WOL relay. Depending on the device used you may need to port forward. Such devices include but are not limited to;
    - Router WOL utility. Many routers offer a WOL utility either usable with just a router app or by port forwarding the router GUI. (If you do the latter be sure to have an EXTREMELY robust login for the router)
    - A RPI. https://www.instructables.com/id/Raspberry-Pi-As-Wake-on-LAN-Server/
    - A remotely accessible system such as a NAS, or similar.
    - An Arduino with a network connection.
- Use a smart plug. You can set the system UEFI/BIOS to power on the system when power is lost and restored. Then when you want to start the system you just turn the smart plug off and on.
- Use an in-system KVM/Remote management board to interact with the system such as: https://geekworm.com/products/pikvm-a8?_pos=1&_sid=333b48621&_ss=r
- Forward and allow through the router firewall port 9 to the Host. This will only work for ~2 hours due to the way IPs work. after such time you __Will__ need to use one of the other methods mentioned above.

## Tips and Tricks
- WOL has a tendency to break when a system is asleep for a prolonged period of time usually due to a very small network hiccup (usually not even noticeable). This is particularly annoying when abroad. One way to get around this is to set the UEFI of the host to wake the system every day at say 1:00 AM, then have a scheduled task in Windows to sleep the system at say 1:05 AM. This will allow the system to re-establish a network connection at least once a day if it happened to break.