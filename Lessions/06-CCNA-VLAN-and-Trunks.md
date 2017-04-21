# VLANs

* Setup by default to be part of vlan 1 (cannot be renamed or deleted)
* Types of VLANs
	* Default VLAN
	* Native VLAN (used for trunk ports)
	* Data VLAN
	* Voice VLAN
	* Management VLAN

## Tips & Tricks

* When possible match your network numbers the the vlans they are on
* Use last port on switch for Management VLAN
* The Management VLAN is often numbered VLAN 99
* Do NOT put an IP address on the default VLAN

## Usage

* show vlan
* conf t
	* vlan 50
		* name example
	* interface range fastEthernet 0/10 12
		* switchport mode access
		* switchport access vlan 50

## Management Interface

* conf t
* interface vlan 99 (access a virtual interface on the switch)
	* ip address 192.168.99.2 255.255.255.0
	* no shutdown
* conf t
	* line vty 0 15
	* password cisco
	* login
* conf t
	* enable secret cisco
