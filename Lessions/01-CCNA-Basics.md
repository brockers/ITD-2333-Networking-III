## Display Router Commands
* ? at any time for a list of available commands
* show interfaces
* show ip route
* show running-config
* show ip interface brief

## Configuration Commands

### Start in User Exec >
* enable (to change to Command mode)

### Command Mode (preveleged exec mode) #
* configure terminal (to change to global config mode)
* copy running-config startup-config
* show running-config
* reload

### Global Configuration Mode (config)#
* line console 0 (to change to Line Config mode for console line 0)
* hostname myhostname
* ip domain-name awesomedomainname.com
* interface fastEthernet 0/0 (to change to Interface Configurtion)
* Ctrl-C (exit to priveleged exec mode)
* no ip domain-lookup (fix pain in the ASS domain lookups)

### Interface Configuration Mode
* description 192.168.250.0/24 network
* ip address 192.168.250.254 255.255.255.0
* no shutdown
* do wr
* Ctrl-C (exit to Global Config mode)

### Line Configuration Mode (config-line)#
* line console 0
* password cisco (set the password equal to cisco)
* login (enable password checking)
* exit (exit to global config mode)

### telnet
* In Global Config
* line vty 0 4 (line configuration mode for virtual terminals 1-5)
* password bobby (set password to bobby)
* login
* exit
* copy run start
* show run