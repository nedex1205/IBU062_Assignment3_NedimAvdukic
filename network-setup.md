The components are:
1 Router
2 Switches
3 Computers
3 Servers
1 Laptop
Added 2 additional pc's afterwards.



To configure DHCP on the router for two networks, do the following:
Configure Router Interfaces:
First, we assign IP addresses to the router interfaces:
    enable 
    configure terminal 
    interface GigabitEthernet0/0 
    ip address 168.90.0.1 255.255.0.0 
    no shutdown 
    exit
This interface is connected to the first network with IP address 168.90.0.1 with a subnet mask of 255.255.0.0 and the second network has an IP address of 210.3.14.1 with a subnet mask 255.255.255.0.

Enable DHCP for Each Network:
    To assign IP addresses dynamically to the devices in both networks, configure two DHCP pools:

    ip dhcp pool NET1 
    network 168.90.0.0 255.255.0.0 
    default-router 168.90.0.1
    exit
This command configures the DHCP pool NET1 for the first network with the default router as 168.90.0.1.


    ip dhcp pool NET2 
    network 210.3.14.0 255.255.255.0 
    default-router 210.3.14.1
    exit
This command configures the DHCP pool NET2 for the first network with the default router as 210.3.14.1.

After these steps go through each node and manually set the Gateway to DHCP