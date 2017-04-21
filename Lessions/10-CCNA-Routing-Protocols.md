# Routing Protocols

Protocals used by routers to exchanges routes with other routers VS Routed Protocal such as TCP/IP routable/routed protocol.

Terms: Administration Distance (AD) and hop count

## IGP

Interior Gatway Protocols

* RIP
* RIPv2
* EIGRP (Cisco propriatary protocal)
* OSPF (Open Sortest Path First)
* ISIS (CCNP topic)
* RSVP ??

## EGP 

Exterior Gatway Protocal

* BGP
	* Boarder Gateway Protocal (ISP-to-ISP, CCNP topic)

## Distance Vector

Examples include RIP, RIPv2, IGRP, EIGRP

Routers communicate with neighbor rouers advertising network as measure of distance (aka hop count) and vectors (which interfaces)  Generally the routers will only "know" about attached routers and their routes.

Best Use:

* Simple networks
* Flat networks
* Non-hierarchical networks
* Easier to configure


## Link State

Examples include OSPF & ISIS

Router communicate with all other routers exchainging link-state information (connections to other routers) and build a topology of the entire network.  This provides a complete view of the newtwork to the routers allowing for optimation of routes.

Best Use:

* Large Networks
* Hierarchical Networks
* Harder to configure
* Sync time between routers is faster
