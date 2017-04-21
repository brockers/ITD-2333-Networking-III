## Summary Route

Generally useful if you have subnetted your logical network segments into groups.  i.e. all your 172.16.x.x are in the same OSPF area.

To find your route summary you will need to calculate your CIDR value.  This process is the same for 3rd octect or 2nd octect as it is for the 4th.

11111111.11111111.11000000.00000000

Where each bit of your octect has a decending half value:

128 - 64 - 32 - 16 - 8 - 4 - 2 - 1 


To find the summary route for several routes we have to find the common bit between all ip ranges:

	10.0.1.0
	10.0.2.0
	10.0.3.0
	10.0.8.0

Converted into binary is:

	00001010.00000000.00000001.00000000
	00001010.00000000.00000010.00000000
	00001010.00000000.00000011.00000000
	00001010.00000000.00001000.00000000

The resulting ip ranges are shared up to the 20th bit. AKA the /20 CIDR.  The third octect /20 CIDR has a value of 240:

	128 + 64 + 32 + 16 = 240

## Command

So on the Bountry Router we run the following command 

* conf t
* router ospf 1
* area 1 range 10.0.0.0 255.255.240.0
