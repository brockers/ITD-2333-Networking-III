## Loopback Interface Configuration

Creates a virtual network interface that will capture routed traffic.  Useful for testing and configuration.

## Create Loopback

* conf t 
* inteface loop 0
* ip address 172.18.0.0 255.255.0.0

Interface will automatically come up, no shutdown is unnecessary

## Remove Loopback

* Shutdown interface
    * config t
    * int loop 0
    * shutdown
* Remove Interface
    * no int loop 0

Make sure to save your work.

