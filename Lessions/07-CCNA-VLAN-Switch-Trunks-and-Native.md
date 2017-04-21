# VLAN Trunks

Technically dynamic trunking protocal (DTP is supposed to be enable on 2650 switches to support 802.1q but don't trust it.  Trunking only works on switches that support 802.1q and trunked traffic that doesn't get tagged will automatically get passed to the native VLAN.  The native VLAN doesn't get tagged through the trunk either.

## Setup Trunk (on both switches)

	* interface fa0/1
	* switchport mode trunk
	* switchport trunk allowed vlan 1-99
	
### Verify
	
	* show run
	* show vlan
	* show interface trunk
	* show interfaces fa0/1 switchport
	
## Configure Native VLAN (on both switches)

	* vlan 80
	* name native
	* interface fa0/1
	* switchport trunk native vlan 80
	
### Verify

	* show interface trunk
	* show interfaces fa0/1 switchport