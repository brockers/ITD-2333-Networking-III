## GRE Tunnel

WARNING: This is an un-encrpyted tunnel.

### Configure R1

* en
* conf t
* interface tun0
* ip address 10.2.2.1 255.255.255.0 
	* This is a virtual network between the two networks... a tunnel network.
* tunnel source fa0/0
	* Outbound interface of THIS router
* tunnel destination 54.134.29.54 
	* External Interface Address of our destination router
* tunnel mode gre ip

Then connect the route just like the routers are directly connected

* ip router 10.3.3.0 255.255.255.0 10.2.2.2
* do wr

### Configure R2

Now setup the second router.

* interface tun 0
* ip address 10.2.2.2 255.255.255.0
* tunnel source fa0/0
* tunnel destination 97.232.5.35
* tunnel mode gre ip
* ip router 10.1.1.0 255.255.255.0 10.2.2.1

