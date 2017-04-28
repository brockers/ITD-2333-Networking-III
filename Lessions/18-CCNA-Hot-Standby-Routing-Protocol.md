## HSRP 

Basically we setup a virtual gateway address between two routers on the same network.  In actuality the routers interface IP never changes. 

Note, that HSRP does not do load balancing.  You need to implement GLBP if you are wanting load-balancing.

### Setup

Setup TWO routers on through another network.  Setup routes so they can reach eachother (or at least their outside interfaces.) 

### R1

* conf t
* interface fa0/0
* standby 1 ip 10.0.0.1
* standby 1 priority 105
* standby 1 preempt
	* if the active router returns from a failed state return back to THIS router as the new active
* standby 1 track int fa0/1
	* this would be the interface going out to our default route
	* when this interface goes down, the priority value will drop 10 points, thereby making the other router a higer priority.  When the conneciton comes back up, the priority would return to us.

### R2

* conf t
* int fa0/0
* standby 1 ip 10.0.0.1
* standby 1 track int fa0/1
* standby 1 priority 100 (this is the default and not entirely necessary.)

