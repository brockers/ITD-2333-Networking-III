# Routing Protocols RIP

## RIP v1

Simple and easy to config.  Provides routing information to attached routers but only classful networks.  i.e. RIP doesn't understand subnet masks.

* conf t
* router rip
* network 192.168.1.0 

In the above example 192.168.1.0 is the network you want to advertise in RIP.  To disable traffic on other interfaces

* passive-interface fastEthernet 0/1

## RIP v2

Same functionality as v1 but with the ability to enable subnetting (a functionality called autosummary)

* config t
* router rip 
* version 2
* no auto-summary