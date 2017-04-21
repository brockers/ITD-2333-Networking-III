## Backup tftp

* en
* copy running-config tftp://10.0.0.35/config-file-name
	OR
* copy running-config tftp:
	* enter destination IP
	* enter file-name you want to save
	
## Restore tftp

First you will need access to the network the tftp server is running on.

* conf t
* interface fa 0/0
* ip address 10.0.0.1 255.255.255.0
* no shutdown

Then run the copy command in reverse.  You are expected to the filename

* en
* copy tftp://10.0.0.35/config-file-name running-config
	OR
* copy tftp: running-config
	* enter destination IP
	* enter file-name you want to save