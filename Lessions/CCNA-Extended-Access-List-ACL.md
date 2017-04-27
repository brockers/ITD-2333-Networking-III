## ACL

Access lists are basically firewall rules that allow you to allow/block traffic to different parts of your network based on a number of rules.  

Entended Access Lists work differently from Standard Access Lists in that they allow/block traffic from source ip, destination ip, OR entire ports.

Extended ACL that are numbered 100-199 and applied closes to the source.

The Struture of an Extended Access List rule is:

	access-list [100-199] action ip/tcp/etc SOURCE DESTINATION

### Create ACL

* conf t
* access-list 100 deny ip 10.0.0.100 0.0.0.0 172.16.0.0 0.0.0.255
* access-list 100 permit ip any any

This will block traffic from (source) 10.0.0.100 to (aka destination) 172.16.0.0/24

### Apply ACL

* int fa0/0
* ip access-group 100 in

### Special Rules

#### Inherited ACL Rules

* There is a default deny any any *just like* in Standard ACL.
* Rules are processed top to bottom.
* More general rules should be created after more specific rule.

#### New Options

When a protocal is specificed a particular port number is included using a qualifier.

   option  |   meaning
  -------------------------
     eq    | equals
     gt    | greater than
     lt    | less than
   range   | range of ports 


### Advanced Rules

#### Allow Interet Ports 

Using Default deny for all other traffic.  
* conf t
* access-list 100 permit tcp 10.0.0.0 0.0.0.255 host 192.168.1.100 eq 80

#### Block OSPF Except to our 10.0.0.128/25 Network

Allow all other (non OSPF traffic)

* access-list 100 permit ospf any 10.0.0.128 0.0.0.127
* access-list 100 deny ospf any any
* access-list 100 permit any any

#### Allow TCP Ports 100-200

Block all others with explicit rule.

* access-list 100 permit tcp any any range 100 200
* access-list 100 deny any any

