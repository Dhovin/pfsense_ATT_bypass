# pfsense AT&T bypass
Setup for bypassing the AT&T router using pfsense 23.05 and newer

## Requirements:
- 4 NIC ports
  - Intel controller prefered
  - two either builtin or PCIe (other two can be USB since they are outof band)
- pfsense 23.05 or newer

## Sources: 
- https://docs.netgate.com/pfsense/en/latest/recipes/authbridge.html
- https://support.adamnet.works/t/running-on-a-transparent-pfsense-bridge/79

## Instructions:
1. Disable Outbound NAT
   - Firewall > NAT > Outbound
   - Change Outbound NAT Mode to Disabled
2. Disable Member Filter and Enable Bridge Filtering
   - System > Advanced > System Tunables
   - Find *net.link.bridge.pfil_bridge* and edit value to *1*
   - Find *net.link.bridge.pfil_member* and edit value to *0*
3. Turn on Ethernet Filtering
   - System > Advanced > Firewall & NAT
   - scroll down and enable Ethernet Filtering
4. Create the bridge
   - Interface > Bridges
   - Create a new bridge and add the WAN and LAN interfaces
5. Create new port with new bridge
   - Interfaces > Interface Assignments
   - Select the new bridge in the bottom dropdown and click +Add
6. Disable DHCPv6 and DHCP RA on LAN
   - Services > DHCPv6 Server & RA > LAN
   - Select DHCPv6 Server, uncheck Enable DHCPc6 Server on interface LAN, and click Save
   - Select Router Advertisements, change Router Mode to Disabled and click Save
7. Create modem interface
   - Interface > Assignments
   - 
