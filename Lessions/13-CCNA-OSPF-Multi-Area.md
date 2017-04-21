## OSPF

* Large large networks
		* ASBR, Autonmous System Boundry Router (i.e the gateway for all routers)
		* Border routers, or routers that attach to 2 or more areas.
		* Border routers and the ASBR make up your backbone routers
		* Internal routers, routers solely inside a network, make up the majority of the network
* Defines a hierachy of the networks
* Then each hierachy master summaries the path lengths and sends them "upstream"
* Network must be well defined
* Required a mutli-layer hiarchy;
	* Backbone Area 0
		* Border routers should exist in no more than 3 areas 
	* Non-backbone Areas
		* Must connect directly to area 0
		* Should design address scheme for contiguous subnets
		* No more than 50 per area

### ISP

* conf t
* hostname ISP
* int g0/0
* ip address 111.111.111.1 255.255.255.240
* no shutdown
* ip router 0.0.0.0. 0.0.0.0 g0/0
* do wr

## ASBR Router

* IP Interface
	* conf t
	* hostname ASBR
	* inter fa 0/0
	* ip address 111.111.111.2 255.255.255.240
	* no shutdown
	* do wr
* Border Router Interface
	* inter fa 1/0
	* ip address 10.0.0.1 255.255.255.252
	* no shutdown
	* do wr
* Default Route
	* ip router 0.0.0.0. 0.0.0.0 fa 0/0
* OSPF
Remember your ISP connection will NOT participate in OSPF. The default-information makes this the ASBR.
	* global config
	* router ospf 1
	* router-id 3.3.3.3
	* network 10.0.0.0 0.0.0.3 area 0
		OR
	* network 10.0.0.1 0.0.0.0  area 0
	* default-information originate

## Area Border Router

* First interface
	* conf t
	* hostname ABR1
	* int fa 1/0
	* ip address 10.0.0.2 255.255.255.252
	* no shutdown
* Second Interface
	* interface fa 0/0
	* ip address 192.168.0.1 255.255.255.0
	* no shutdown
* OSPF
	* router ospf 1
	* router-id 2.2.2.2
	* network 10.0.0.2 0.0.0.0 area 0
		OR
	* network 10.0.0.0 0.0.0.3 area 0
	* network 192.168.0.0 0.0.0.255 area 1
		OR
	* network 192.168.0.1 0.0.0.0. area 1

