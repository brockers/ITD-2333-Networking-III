## Advanced VLAN

Voice VLAN is typically on VLAN 150

* vlan 150
	* name voice
* switchport mode access
* switchport access vlan 150

## Route Trunking

### On switch port going to router

* switchport mode trunk
* switchport trunk allowed vlan 1-99,150
* switchport trunk native vlan 80

### on the router

Setting up router for mutliple vlans on a trunk, via sub-interfaces

* interface fa0/0.1
* encapsulation dot1q 1
* ip address 192.168.1.1 255.255.255.0
* inteface fa0/0.50
* encapsulation dot1q 50
* ip address 192.168.50.1 255.255.255.0
* inteface fa0/0.80
* encapsulation dot1q 80
* ip address 192.168.80.1 255.255.255.0
* etc.. etc.. etc..
* end
* inteface fa0/0
* no shutdown