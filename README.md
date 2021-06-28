# Firewall-and-Site-to-Site-VPN-Configuration
A project I completed at NJIT. Goes over how to set up pfSense firewalls in a client-server relationship over the internet.

## About
This project contains 4 VMs created in VirtualBox, a client, a server, and 2 pfSense firewalls. The client and the server were on two different subnets. The client and the server were only allowed to communicate through a third, mock "Internet" subnet through the pfSense firewalls. Site to Site VPN can be configured in the pfSense firewalls.

The best way to go about using this project would be to donwload the paper and follow along with the instructions contained in the paper. You can use any Linux distibution, and you can go to [pfSense.com](https://www.pfsense.org/download/) to download the free firewall software.

## Tasks
### Task 1–Basic Configuration:
- Download and install two instances of pfSense in a virtual environment (https://www.pfsense.org/download/)
- Download and install two instances of your favorite Linux distribution in a virtual environmentThe server should have a web server and SSH server installed and operational
- Configure the virtual networks and associated network interfaces as per the diagram

### Task 2 –Basic Security Configuration:
- Configure access rules on both firewalls so that the client can connect to the server on TCP/80 but cannot access SSH.  (If you don’t have a GUI installed on the Client, you can use Lynx)
- Configure access rules on the Site B Firewall so that no unsolicited connections can be made from the Server network to the Client network. 
- Note:  the client and server will be able to communicate because we are using a private address range for the outside network (e.g. the “Internet”).  In the “real world” the ISP would refuse to carry the packets from either site because they are using RFC1918 private IP addresses.  To make this work, we need to configure NAT.
 
### Task 3 –Basic Network Address Translation (NAT) Configuration:
- Configure NAT rules on the site A firewall so that packets from the inside interface have their source addresses translated to the IP address of the outside interface.  Also configure NAT rules on the site B firewall so that the server is “published” to the IP address of the outside interface.  That is, the client will now be connecting to port 80 of the IP address of the outside interface of the site B firewall, not the server’s IP.  Remember, in the real world, the client network and the server network use private IP addresses.  The server won’t be reachable and therefore will need to have its IP address mapped to an IP address that is routable on the Internet.  Show a packet trace from the server that shows that arriving packets have the source address ofthe outside interface of the site A firewall and not the address of the client.  Show a packet trace from the client that shows an established connection HTTP connection to the site B firewall’s outside interface. You can introduce an additional virtual machine between the two firewall’s outside interfaces specifically for the purpose of packet tracing, or you can use the built-in firewall tools.

### Task 4–Basic Site-to-Site VPN Configuration:
- Modify your configuration so that both the client network and the server network can communicate using IPsec.  That is, establish a VPN tunnel between the site A and site B firewalls.  Communication between the client and server should be carried through this tunnel.  Use the strongest available security settings for both security associations.  Provide screenshots and packet traces to prove that your VPN is operating properly.
