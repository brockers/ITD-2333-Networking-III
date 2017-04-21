# NTP
	
	* configure mode (to config)
		* ntp server ip-of-server
		* ntp update-calendar
	* exec mode (verify)
		* show ntp status
		
# Syslog

	* configure mode (to config)
		* service timestamps log datetime msec
		* logging host ip-of-server
	* exec mode (to verify)
		* show logging
		
# SSH

	* ip domain-name awesomedomainname.com
	* Create users
		* username admin privilege 15 secret password
	* Setup Virtual Terminals
		* line vty 0 4 (configure all 5 at the same time)
		* login local
		* trasport input ssh
	* Remote Old Keypairs
		* crypto key zeroize rsa
	* Create New Keypairs
		* crypto key generate rsa
	* Setup other SSH Settings ```Not really working for some reason```
		* ip ssh time-out 90
		* ip ssh authentication-retries 2
		* ip ssh version 2

## Verify

	* On a laptop (servers seems to lack the client)
	* ssh -u admin 1.2.3.4