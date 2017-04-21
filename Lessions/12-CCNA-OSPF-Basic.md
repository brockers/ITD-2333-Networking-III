# OSPF

You will need to choose a router id scheme.  The router id is a unique ip-like number for each router in your ospf network (ex: 1.1.1.1).  Additionally you will want to set the default route on your ASBR to your upstream.

The other thing you will need is to be able to calculate the inverse netmask (called the wildcard mask.)  This is simply the netmask for the network subtracted by 255.255.255.255.

Example:

	 Netmask         |  Wildcard  
	-----------------|-------------
	 255.255.255.0   |  0.0.0.255 
	 255.255.255.252 |  0.0.0.3
	 255.255.240.0   |  0.0.15.255

## Basic Configuration

* router ospf 1
* router-id 1.1.1.1
* network 10.0.0.2 0.0.0.0 area 0
		OR
* network 10.0.0.0 0.0.0.3 area 0
* network 192.168.0.0 0.0.0.255 area 0
		OR
* network 192.168.0.1 0.0.0.0 area 0

## Testing

* show ip route
* show ip ospf database
