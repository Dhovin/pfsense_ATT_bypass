# pfsense AT&T bypass
#### Setup for bypassing the AT&T router using pfsense 23.05 and newer

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
   - Services >
   - 
