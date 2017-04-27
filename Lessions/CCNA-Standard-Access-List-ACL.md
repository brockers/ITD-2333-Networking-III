## ACL

Access lists are basically firewall rules that allow you to allow/block traffic to different parts of your network based on a number of rules.  

Standard access list work specifically by blocking/allowing based on sourceip address.  Standard access lists are numbered 1-99 and applied closes to the destination (as opposed to Extended ACL that are numbered 100-199 and applied closes to the source.)

This just means that the rule should be put on the router (AND INTERFACE) YOU control that is closest to the destination that you are trying to get to.

### Create ACL

* conf t
* access-list 1 deny 172.16.0.0 255.255.255.255
* access list 1 permit any

Notice that the access list deny argument is NOT the subnet mask but is the wildcard bits (i.e. the inverse of the subnet mask.) If you wanted to block just a single ip address the deny rule would look like this:

* access-list 1 deny 172.16.0.100 0.0.0.0

The permit any line changes the default policy for all other traffic to allow it.  So we are only blocking only the IP range we specificed.

### Apply ACL to interface

* int fa0/0
* ip access-group 1 out

### Special Rules

#### ACL Order

Access lists are processes IN ORDER from top to bottom.  When a host matches the line, the rule is applied, and no more rules are processed.  Meaning if you have the following rules:

* access-list 1 deny any
* access-list 1 permit 10.0.0.0 0.255.255.0

And you tried to ping 10.0.0.1 it would fail because rule *deny any* catches ALL traffic, meaning no traffic will ever get processed by our permit rule.

So put specific statements on top and more general at bottom. The following example would be a GOOD rule structure:

* access-list 1 deny host 192.168.1.23 (block a single IP)
* access-list 1 deny 10.0.0.0 255.255.255.0 (block a network)
* access-list 1 permit any (allow remaining traffic)

#### Default Final Rule

The final rule (default ACL) will always be:

* access-list 1 deny any

Even if you don't see it.  So if you want to allow traffic you MUST specify it with a general allow rule.

* access-list 1 permit any

### Remove ACL

* no access-list 1

