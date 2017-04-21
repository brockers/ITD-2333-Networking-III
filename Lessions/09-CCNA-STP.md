# STP (Spanning Tree Protocal)

* A Layer 2 protocal for switches
* Helps network avoid switching loops or broadcast storms
* Used in networks were you have redundant paths that could create loops
* Maximum network size of 7 switches "wide"
* How it works:
	* It identifies redundant paths
	* Determins the fastest paths (via "cost")
	* Turns "off" duplicate paths when not needed

## Usage

View STP 

* switch# show spanning-tree
* switch# debug spanning-tree events

Turn off STP

* switch(config)# no spanning-tree vlan 1

Turn on STP

## Root Bridge

The root bridge is the switch that is at the top of the Spanning Tree.  It is calculated using a "bridge priority number" (by default 32768) plus the VLAN number.  If all switches have identical values the switch with the lowest MAC address wins.  THIS IS BAD.

* Pick the biggest baddest switch in the center of your network.

Manually lower the bridge priority number (must be in increments of 4096)

* switch(config)#spanning-tree vlan 1 priority <num> 
* switch(config)#spanning-tree vlan 1 root primary
* switch(config)#spanning-tree vlan 1 root secondary

Reset with

* spanning-tree vlan 1 priority 32768

## Port "Costs"

* 10G = value 2
* 1G = value 4
* 100M = value 19
* 10M = value 100
* 4M = value 250

Or manually configure it via:

* switch(config)#interface fa0/1
* switch(config-if)#spanning-tree cost <num>

## Port Designations

* Root Port = Port closest to root bridge
* Designated Port = Port being forwarded
* Non-designed Port = Port being blocked

## Other useful Info

See the arp table on a Windows/Linux PC

* arp -a

Bridge and Switch are sometimes used interchangably (a switch is a multiport bridge)

CCNA, do we need to cover PVST+ ??


